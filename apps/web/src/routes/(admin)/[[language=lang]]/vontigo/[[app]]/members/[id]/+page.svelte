<script lang="ts">
	import { page } from '$app/stores';
	import { getToastStore, type ToastSettings, Toast, ProgressRadial } from '@skeletonlabs/skeleton';
	import CompEditor from '$lib/core/core/frontend/components/admin/Editor/CompEditor.svelte';
	import Icon3BottomLeft from '$lib/icons/Icon3BottomLeft.svelte';
	import IconArrowDown from '$lib/icons/IconArrowDown.svelte';
	import IconPlusSmall from '$lib/icons/IconPlusSmall.svelte';
	import { AppBar, AppShell, RadioGroup, RadioItem } from '@skeletonlabs/skeleton';
	import { Drawer, drawerStore } from '@skeletonlabs/skeleton';
	import type { DrawerSettings } from '@skeletonlabs/skeleton';
	import type { PageData } from './$types';
	import { STORE_ADMIN_SITE_URL, isEditorOpen } from '$lib/core/shared/stores/site';
	import type { ReferenceStructure, TableStructure } from '$lib/core/shared/types';
	import { onMount } from 'svelte';
	import RecordDetail from '$lib/core/core/frontend/components/admin/Database/RecordDetail.svelte';

	const toastStore = getToastStore();
	export let data: PageData;
</script>

<div class="max-w-screen-xl mx-auto px-12">
	<AppBar class="sticky top-0 z-10 p-4 bg-white">
		<!-- <svelte:fragment slot="lead">
			<Icon3BottomLeft />
		</svelte:fragment> -->
		<h2 class="text-xl font-bold">Member</h2>
		<span class="uppercase text-sm font-semibold"
			><a href={$STORE_ADMIN_SITE_URL + `/tags/${$page.params.visibility}`}>All members</a> > {$page
				.params.id || ''}</span
		>
		<svelte:fragment slot="trail">
			<!-- <div class="w-full "> -->
			<div class="hidden md:flex md:flex-row-reverse w-full items-center gap-6">
				<!-- <button
					type="button"
					class="btn btn-sm variant-filled rounded"
					on:click={() => {
						selectedPost = null;
						drawerStore.open(settings);
					}}
				>
					<span><IconPlusSmall /></span>
					<span>New post</span>
				</button>
				<div class="filter-bar flex gap-4">
					<span><CompMenuPosts /></span>
					<span><CompMenuMembersAccess /></span>
					<span><CompMenuAuthors /></span>
					<span><CompMenuTags /></span>
					<span><CompMenuSortBy /></span>
				</div> -->
			</div>
			<button type="button" class="md:hidden btn btn-sm variant-filled rounded">
				<span><IconPlusSmall /></span>
				<span>New post</span>
			</button>
			<!-- </div> -->
		</svelte:fragment>

		<!-- <svelte:fragment slot="trail">(actions)</svelte:fragment> -->
	</AppBar>

	{#if data.record}
		<RecordDetail {data} table={'members'} />
	{/if}
</div>
