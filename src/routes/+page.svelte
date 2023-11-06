<script lang="ts">
	const top = 100;

	const base = 25;

	const h = (i: number) => {
		return base - (i + 1) * 2.25;
	};

	const y = (i: number) => {
		return base * i - i * 0.95 + top;
	};
</script>

<svelte:head>
	<link href="https://fonts.googleapis.com/css2?family=Fira+Code&display=swap" rel="stylesheet" />
</svelte:head>

<div class="base">
	<img class="shirt" src="/shirt.svg" alt="" />

	<div class="container">
		<div class="glow" />
		<div class="inner-glow" />

		<div class="strips">
			<div class="grad" />
			<svg viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
				<defs>
					<clipPath id="stripClip">
						<rect x="0" y="0" width="300" height={top} />
						{#each Array(11) as _, i}
							<rect x="0" y={y(i)} width="300" height={h(i)} />
						{/each}
					</clipPath>
				</defs>
			</svg>
		</div>
	</div>
	<h2>how beautiful is this, friends?</h2>
</div>

<style>
	.base {
		display: flex;
		flex-direction: column;
		gap: 2rem;
		justify-content: center;
		align-items: center;
		font-family: sans-serif;
		background-color: rgb(20, 0, 43);
		height: 100vh;
		width: 100vw;
		font-family: 'Fira Code', monospace;
		overflow: hidden;
	}
	.shirt {
		position: absolute;
		scale: 70%;
		translate: 0 150px;
		opacity: 0.4;
	}
	h2 {
		background: linear-gradient(110deg, rgb(249, 194, 50) 0%, rgba(255, 70, 249, 1) 100%);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
	}
	.container {
		position: relative;
		width: 300px;
		height: 300px;
	}
	.strips {
		position: absolute;
		inset: 0;
		clip-path: circle(150px at center);
	}

	.grad {
		position: absolute;
		inset: 0;
		background: linear-gradient(180deg, rgb(249, 194, 50) 0%, rgba(255, 70, 249, 1) 100%);
		clip-path: url(#stripClip);
	}

	.glow {
		position: absolute;
		inset: 20px;
		border-radius: 100%;
		background-color: rgb(255, 0, 115);

		filter: blur(50px);
	}
	.inner-glow {
		position: absolute;
		inset: 40px;
		border-radius: 100%;
		background-color: rgb(255, 0, 115);

		filter: blur(10px);
	}

	:global(body) {
		margin: 0;
		padding: 0;
		overflow: hidden;
	}
</style>
