<script>
  import { onMount } from "svelte";
  import BookGrid from "./bookgrid.svelte";
  import Button from "../common/button.svelte";
  import { httpGet } from "../common/api.js";

  let books = [];
  onMount(async function () {
    const { data } = await httpGet("/?_sort=id&_order=desc");
    books = data;
  });
</script>

<header>
  <span class="preamble">Welcome to the</span>
  <h1>Library</h1>
</header>

<p class="greeting">
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Perferendis, iusto
  aut ipsa quo, sint, fuga praesentium adipisci placeat inventore fugiat
  blanditiis aliquam magni fugit! Porro totam incidunt obcaecati quis fugiat!
</p>

<Button>Add Book</Button>
<BookGrid {books} />

<style>
  header {
    margin: var(--spacingMedium) 0 var(--spacingLarge) 0;
    text-transform: uppercase;
  }
  .preamble {
    display: block;
  }
  h1 {
    font-size: var(--typeSizeXXLarge);
    font-weight: var(--typeWeightBold);
    line-height: var(--typeLineHeightTight);
  }
  .greeting {
    font-size: var(--typeSizeSmall);
  }
</style>
