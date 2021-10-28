<script>
	import { onMount } from "svelte";

	let input;
	let showList = true;

	onMount(() => {});

	function on_ul_click() {
		console.log("on_ul_click");
		input.focus();
	}

	function on_input_blur_sync() {
		console.log("on_input_blur_sync");
	}

	function closeList() {
		showList = false
	}
</script>

<div>
	<input
		placeholder="1. focus me"
		bind:this={input}
		on:blur={() => {
			setTimeout(() => closeList(), 100);
			on_input_blur_sync();
		}}
	/>
	<ul on:click={on_ul_click} class:hidden={!showList}>
		<li>2. click me</li>
	</ul>
</div>

<style>
	.hidden {
		display: none;
	}
	ul {
		background-color: aliceblue;
	}
	li {
		line-height: 60px;
	}
</style>
