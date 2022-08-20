<script lang="ts">
	import { Lightbulb } from 'lucide-svelte';

	let darkMode = '';
	let todoInput = '';
	let todos: string[] = ['a', 'b'];
	const toggleDarkMode = () => {
		darkMode = darkMode === 'dark' ? '' : 'dark';
	};

	const addTodo = () => {
		todos = [...todos, todoInput];
		todoInput = '';
	};

	const removeIndex = (i: number) => {
		todos.splice(i, 1);
		todos = todos;
	};
</script>

<div class={darkMode}>
	<div class="bg-gray-100 dark:bg-gray-800 h-screen pt-20">
		<div class="max-w-lg mx-auto bg-white rounded-md shadow-md p-2 flex flex-col gap-4">
			<div class="flex justify-between">
				<h1 class="font-bold text-lg">Todo App</h1>
				<div on:click={toggleDarkMode} class="cursor-pointer">
					<Lightbulb color="black" />
				</div>
			</div>
			<div>
				<div class="flex">
					<input
						bind:value={todoInput}
						class="flex-grow border-gray-200 border-[1px] rounded-tl-md rounded-bl-md"
						type="text"
					/>
					<button
						on:click={addTodo}
						class="bg-purple-400 py-2 px-4 rounded-tr-md rounded-br-md text-white"
						type="submit">Add</button
					>
				</div>
			</div>
			<div>
				{#each todos as todo, i}
					<div class="bg-gray-100 p-2 mb-2 flex items-center justify-between">
						<div class="flex">
							<input type="checkbox" name="" id="" class="mr-2" />
							<p>{todo}</p>
						</div>
						<p on:click={() => removeIndex(i)}>X</p>
					</div>
				{/each}
			</div>
		</div>
	</div>
</div>
