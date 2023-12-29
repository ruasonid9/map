<!-- Script -->
<script lang="ts">
// Imports
import map2020 from "$lib/maps/2020.png";
import map2023 from "$lib/maps/2023.png";

// Variables
const maps = {
	"2020": map2020,
	"2023": map2023
};
const years = Object.keys(maps);
let index = 0;
$: map = maps[years[index] as keyof typeof maps];
</script>

<!-- Template -->
<main>
	<div id="container">
		<img id="map" src="{map}" alt="map">
	</div>
	<div id="timelapse">
		<input id="slider" type="range" min="0" max="{years.length - 1}" bind:value={index}>
		<span id="label">{years[index]}</span>
	</div>
</main>

<!-- Style -->
<style>
/* Defaults */
* {
	color: rgb(var(--cm-wt));
}

:global(body) {
	background-color: rgb(var(--cm-bk));
}

/* Container */
#container {
	align-items: center;
	background-color: rgba(var(--cm-bkl), 0.8);
	border-radius: 5px;
	display: flex;
	height: 60vh;
	justify-content: center;
	margin: 5vh 5vw;
	padding: 25px 25px;
}

#map {
	height: 100%;
	object-fit: contain;
	width: 100%;
}

/* Timelapse */
#timelapse {
	align-items: center;
	display: flex;
	flex-direction: row;
	gap: 25px;
	justify-content: center;
	margin: 5vh 5vw;
}

#slider {
	width: 50vw;
}

#label {
	font-weight: bold;
}

@media screen and (max-width: 750px) {
	#container {
		height: 25vh;
	}
}
</style>
