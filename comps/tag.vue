<template>
  <span v-if="!href" class="common-tag" :class="{active,}" @click="$emit('click', $event)"><slot/></span>
  <NuxtLink v-else class="common-tag" :to="href"><slot/></NuxtLink>
</template>

<script>
export default {
  name: "the-tag",
  props: {
    href: String,
    active: Boolean
  }
}
</script>

<style lang="scss">
@use "sass:math";

$size: 1.6rem;
$color: #eaeaea;
.common-tag {
  background: $color;
  border-radius: 4px 0 0 4px;
  color: #626262;
  display: inline-flex;
  align-items: center;
  height: $size;
  padding: 0 1.3rem;
  position: relative;
  cursor: pointer;
  transition: all .1s linear;
  font-size: math.div($size, 2);
  line-height: math.div($size, 2);
  text-decoration: none;
  word-break: keep-all;
  &:after, &:before {
    content: '';
    background: #fff;
    position: absolute;
    transition: all .1s linear;
  }
  &:before {
    border-radius: 10px;
    box-shadow: inset 0 1px rgb(0 0 0 / 25%);
    height: 6px;
    left: 8px;
    width: 6px;
    top: math.div($size, 2);
    transform: translateY(-50%);
  }
  &:after {
    border-bottom: math.div($size, 2) solid transparent;
    border-left: 10px solid $color;
    border-top: math.div($size, 2) solid transparent;
    right: 0;
    top: 0;
  }
  &:hover{
    background-color: #d7d7d7;
    color: black;
    &:after {
      border-left-color: #d7d7d7;
    }
  }
  &.active{
    background-color: #20bcd1;
    color: white;
    &:after {
      border-left-color: #20bcd1;
    }
  }
}
</style>
