<template>
	<button
		class="t-button"
		:class="{
			't-button__primary': !outline,
			't-button__primary-warning': !outline && warning,
			't-button__primary-danger': !outline && danger,
			't-button__disabled': disabled,
			't-button__outline': outline,
			't-button__outline-danger': outline && danger
		}"
		:disabled="disabled"
		:style="{
			...spacingProps
		}"
	>
		<slot />
	</button>
</template>

<script>
import spacingProps from "../../mixins/spacingProps";

export default {
	name: "TButton",
	mixins: [spacingProps],
	props: {
		color: {
			type: String,
			default: undefined
		},
		outline: {
			type: Boolean,
			default: false
		},
		warning: {
			type: Boolean,
			default: false
		},
		disabled: {
			type: Boolean,
			default: false
		},
		loading: {
			type: Boolean,
			default: false
		},
		danger: {
			type: Boolean,
			default: false
		}
	}
};
</script>

<style lang="sass">
.t-button
	cursor: pointer
	opacity: 1
	font:
		family: inherit
		size: 0.875rem
	outline: none
	user-select: none
	text-align: center
	display: inline-block
	padding: .5rem 1rem
	line-height: 1.2
	border:
		width: 1px
		style: solid
		radius: 2rem

	&__primary
		color: #ffffff
		border-color: #00adb5
		background-color: #00adb5

		&-warning
			background-color: #e5d570
			border-color: #e5d570

		&-danger
			background-color: #f04747
			border-color: #f04747

	&__outline
		border-color: #00adb5
		color: #00adb5
		background-color: #ffffff

		&-danger
			border-color: #f04747
			color: #f04747

	&__disabled
		opacity: .6
		cursor: not-allowed
</style>
