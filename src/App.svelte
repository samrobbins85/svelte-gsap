<script>
  import { gsap } from "gsap";
  import { onMount } from "svelte";
  import Snowman from "./lib/Snowman.svelte";
  let animation = gsap.timeline();

  onMount(() => {
    animation
      .to("#hat", { duration: 1, y: 0 })
      .to("#faceShadow", { duration: 0, opacity: 100 })
      .to("#XMLID_12_", { duration: 0.7, y: -6 }, "+=1")
      .to("#XMLID_14_", { duration: 0.7, y: -1 }, "<")
      .to("#XMLID_17_", { duration: 0.7, y: 1 }, "<")
      .to("#XMLID_18_", { duration: 0.7, y: -1 }, "<")
      .to("#XMLID_19_", { duration: 0.7, y: -6 }, "<")
      .to(
        "#rightArm",
        { duration: 0.7, rotation: 5, yoyo: true, repeat: 3 },
        "+=0.5"
      );
  });
  let light = "#f74b71";
  let dark = "#dd3e68";
  let cybsafe = false;
  function changeColour() {
    if (cybsafe) {
      light = "#f74b71";
      dark = "#dd3e68";
      cybsafe = false;
    } else {
      light = "#3ab0a5";
      dark = "#21837f";
      cybsafe = true;
    }
  }
  function replayAnimation() {
    animation.play(0);
  }
</script>

<main>
  <h1>Merry Christmas!</h1>
  <div class="buttons">
    <button on:click={changeColour}
      >{!cybsafe ? "Get CybSafe" : "Get Festive"}</button
    >
    <button on:click={replayAnimation}>Replay Animation</button>
  </div>
  <div class="svgWrapper">
    <Snowman {light} {dark} />
  </div>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }
  @font-face {
    font-family: Christmas;
    src: url(PWHappyChristmas.woff2) format("woff2");
  }
  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }
  .svgWrapper {
    display: flex;
    justify-content: center;
  }
  .buttons {
    padding-bottom: 2rem;
  }
  button {
    background-color: #f5c25b;
    border: 2px solid #f59e5b;
    padding: 0.5rem 1rem;
    border-radius: 5px;
  }
  button:hover {
    cursor: pointer;
  }

  h1 {
    font-weight: 600;
    font-size: 5rem;
    text-align: center;
    font-family: Christmas;
    color: #a84545;
  }
</style>
