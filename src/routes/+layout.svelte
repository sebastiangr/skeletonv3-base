<script lang="ts">
	import '../app.css';
	import { Sun, Moon } from 'lucide-svelte'; // Importing icons
	let { children } = $props();
	let isDarkMode = $state(false);
  import { Tabs } from '@skeletonlabs/skeleton-svelte';

	function toggleDarkMode() {
		isDarkMode = !isDarkMode;
		document.documentElement.classList.toggle('dark', isDarkMode);
	}

  let group = $state('plane');
  const lorem =
    'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nostrum veniam reprehenderit eum, reiciendis obcaecati, excepturi nemo ipsa fugit suscipit autem vitae numquam et cumque praesentium vero eos minus itaque. Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nostrum veniam reprehenderit eum, reiciendis obcaecati, excepturi nemo.';

</script>

<header class="bg-gray-800 p-4 text-white">
	<nav class="container mx-auto flex justify-between items-center">
		<a href="/" class="text-xl font-bold">MyApp</a>
		<ul class="flex space-x-4">
			<li><a href="/user" class="hover:underline">User</a></li>
			<li><a href="/services" class="hover:underline">Services</a></li>
			<li><a href="/contact" class="hover:underline">Contact</a></li>
		</ul>
		<button onclick={toggleDarkMode} class="bg-gray-700 text-white p-2 rounded">
			{#if isDarkMode}
				<Sun class="w-5 h-5" />
			{:else}
				<Moon class="w-5 h-5" />
			{/if}
		</button>
	</nav>
</header>

<main class="container mx-auto mt-4">
  {@render children()}

  <div class="space-y-4">
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-primary-500">Button</button>
      <button type="button" class="btn preset-tonal-primary">Button</button>
      <button type="button" class="btn preset-outlined-primary-500">Button</button>
    </div>
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-secondary-500">Button</button>
      <button type="button" class="btn preset-tonal-secondary">Button</button>
      <button type="button" class="btn preset-outlined-secondary-500">Button</button>
    </div>
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-tertiary-500">Button</button>
      <button type="button" class="btn preset-tonal-tertiary">Button</button>
      <button type="button" class="btn preset-outlined-tertiary-500">Button</button>
    </div>
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-success-500">Button</button>
      <button type="button" class="btn preset-tonal-success">Button</button>
      <button type="button" class="btn preset-outlined-success-500">Button</button>
    </div>
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-warning-500">Button</button>
      <button type="button" class="btn preset-tonal-warning">Button</button>
      <button type="button" class="btn preset-outlined-warning-500">Button</button>
    </div>
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-error-500">Button</button>
      <button type="button" class="btn preset-tonal-error">Button</button>
      <button type="button" class="btn preset-outlined-error-500">Button</button>
    </div>
    <div class="flex gap-4">
      <button type="button" class="btn preset-filled-surface-500">Button</button>
      <button type="button" class="btn preset-tonal-surface">Button</button>
      <button type="button" class="btn preset-outlined-surface-500">Button</button>
    </div>
  </div>


  <Tabs value={group} onValueChange={(e) => (group = e.value)} fluid>
    {#snippet list()}
      <Tabs.Control value="plane">Plane</Tabs.Control>
      <Tabs.Control value="boat">Boat</Tabs.Control>
      <Tabs.Control value="car">Car</Tabs.Control>
    {/snippet}
    {#snippet content()}
      <Tabs.Panel value="plane">Plane Panel - {lorem}</Tabs.Panel>
      <Tabs.Panel value="boat">Boat Panel - {lorem}</Tabs.Panel>
      <Tabs.Panel value="car">Car Panel - {lorem}</Tabs.Panel>
    {/snippet}
  </Tabs>
</main>
