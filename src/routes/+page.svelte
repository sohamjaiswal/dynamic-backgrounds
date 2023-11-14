<script lang="ts">
	import { imageBg } from "$lib/stores/stores";
	let newBg: HTMLInputElement;
	const handleSubmit = (e: Event) => {
		if (newBg.value.endsWith(".png") || newBg.value.endsWith(".jpg") || newBg.value.endsWith(".jpeg") || newBg.value.endsWith(".gif") || newBg.value.endsWith(".webp")) {
			$imageBg = newBg.value;
		} else {
			alert("Please enter a valid image URL");
		}
	};
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">
			Enter a URL to update the background image of the page
		</h2>
		<form class="flex flex-col items-center gap-4 card card-hover p-4" on:submit|preventDefault={handleSubmit}>
			<input class="input" type="text" placeholder="Enter image URL" bind:this={newBg} />
			<button class="btn variant-filled-primary" type="submit">
				Update BG to URL
			</button>
		</form>
	</div>
</div>

<style lang="postcss">
	figure {
		@apply flex relative flex-col;
	}
	figure svg,
	.img-bg {
		@apply w-64 h-64 md:w-80 md:h-80;
	}
	.img-bg {
		@apply absolute z-[-1] rounded-full blur-[50px] transition-all;
		animation: pulse 5s cubic-bezier(0, 0, 0, 0.5) infinite,
			glow 5s linear infinite;
	}
	@keyframes glow {
		0% {
			@apply bg-primary-400/50;
		}
		33% {
			@apply bg-secondary-400/50;
		}
		66% {
			@apply bg-tertiary-400/50;
		}
		100% {
			@apply bg-primary-400/50;
		}
	}
	@keyframes pulse {
		50% {
			transform: scale(1.5);
		}
	}
</style>
