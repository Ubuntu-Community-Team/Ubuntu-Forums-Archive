---
title: "Totem Movie Player instant crash"
date: 2009-07-14
forum: Multimedia Software
---

### Post by hetx on 2009-07-14
I looked around for similar problems but I can't seem to weed them out. In my case ONLY the Totem Movie Player crashes, it doesn't matter if I try to play a video with it or just start it using the menu. The window pops up and disappears right away. I can still watch video with VLC but it's bugging me! Grateful for any help!

Ubuntu 9.04

---

### Post by hetx on 2009-07-14
I'd be happy to give more info if I just knew where to look... Also Rythmbox wont start anymore.

Both give "Segmentation fault" when I run them in terminal.

totem --debug wont give me anything but Segmentation fault, but rhythmbox -d did

```
erik@edu:~$ rhythmbox -d
(13:57:40) [0x8617408] [rb_debug_init_match] rb-debug.c:215: Debugging enabled
(13:57:40) [0x8617408] [main] main.c:187: initializing Rhythmbox 0.12.0
(13:57:40) [0x8617408] [rb_threads_init] rb-util.c:388: GMutex isn't recursive
(13:57:40) [0x8617408] [main] main.c:195: going to create DBus object
(13:57:40) [0x8617408] [main] main.c:266: Going to create a new shell
(13:57:40) [0x8617408] [rb_shell_constructor] rb-shell.c:1347: Constructing shell
(13:57:40) [0x8617408] [construct_db] rb-shell.c:1000: creating database object
(13:57:40) [0x8617408] [rb_find_user_file] rb-file-helpers.c:199: found user dir path for 'rhythmdb.xml': /home/erik/.local/share/rhythmbox/rhythmdb.xml
(13:57:40) [0x8617408] [construct_widgets] rb-shell.c:1067: shell: initializing shell services
(13:57:41) [0x8617408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3122: setting playing source to (nil)
(13:57:41) [0x8617408] [rb_shell_player_sync_with_source] rb-shell-player.c:2938: playing source: (nil), active entry: (nil)
(13:57:41) [0x8617408] [rb_header_sync] rb-header.c:460: syncing with entry = <null>
(13:57:41) [0x8617408] [rb_header_sync] rb-header.c:536: not playing
(13:57:41) [0x8617408] [rb_shell_player_sync_control_state] rb-shell-player.c:2450: syncing control state
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1680 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1610 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:659: disposing query model 0x86c1680
(13:57:41) [0x8617408] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:707: finalizing query model 0x86c1680
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x890f488 ()
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x890f588 (Track)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x890f688 (Title)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45010 (Genre)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45110 (Artist)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45210 (Album)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45310 (Year)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45410 (Time)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45510 (Quality)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45610 (Rating)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a45710 (Play Count)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a480d0 (Last Played)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a481d0 (Date Added)
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 0 - reusing parent model
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 1 - reusing parent model
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 2 - reusing parent model
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1358 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1358 chaining to base model 0x86c1610
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 0 - reusing parent model
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 1 - reusing parent model
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 2 - reusing parent model
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c12e8 chaining to base model (nil)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a4f8d0 (Play Queue)
(13:57:41) [0x8617408] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:659: disposing query model 0x86c12e8
(13:57:41) [0x8617408] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:707: finalizing query model 0x86c12e8
(13:57:41) [0x8617408] [rb_sourcelist_append] rb-sourcelist.c:1128: inserting source 0x89f7860 to group library
(13:57:41) [0x8617408] [rb_proxy_config_init] rb-proxy-config.c:114: watching HTTP proxy configuration
(13:57:41) [0x8617408] [get_proxy_config] rb-proxy-config.c:259: HTTP proxy is disabled
(13:57:41) [0x8617408] [rb_shell_constructor] rb-shell.c:1367: shell: setting up tray icon
(13:57:41) [0x8617408] [tray_destroy_cb] rb-shell.c:3000: creating new tray icon
(13:57:41) [0x8617408] [rb_tray_icon_init] rb-tray-icon.c:231: setting up tray icon
(13:57:41) [0x8617408] [rb_tray_icon_show_notifications_changed_cb] rb-tray-icon.c:629: show notifications clicked for 0x8a5b010
(13:57:41) [0x8617408] [tray_destroy_cb] rb-shell.c:3009: done creating new tray icon 0x8a5b010
(13:57:41) [0x8617408] [rb_shell_constructor] rb-shell.c:1370: shell: adding gconf notification
(13:57:41) [0x8617408] [rb_shell_constructor] rb-shell.c:1402: shell: syncing with gconf
(13:57:41) [0x8617408] [rb_source_set_property] rb-source.c:623: Setting Play Queue visibility to 1
(13:57:41) [0x8617408] [visibility_notify_cb] rb-sourcelist.c:1034: Source visibility changed: Play Queue
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c12e8 chaining to base model (nil)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6e858 (Track)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6e958 (Title)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6ea58 (Genre)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6eb58 (Artist)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6ec58 (Album)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6ed58 (Year)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6ee58 (Time)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a6ef58 (Quality)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a740b0 (Play Count)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a741b0 (Location)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_browser_source_state_prefs_sync] rb-browser-source.c:785: syncing state
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1680 chaining to base model (nil)
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 0 - reusing parent model
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 1 - reusing parent model
(13:57:41) [0x8617408] [rebuild_child_model] rb-library-browser.c:696: no selection for browser 2 - reusing parent model
(13:57:41) [0x8617408] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:659: disposing query model 0x86c12e8
(13:57:41) [0x8617408] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:707: finalizing query model 0x86c12e8
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rb_property_view_selection_changed_cb] rb-property-view.c:838: selection changed
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c12e8 chaining to base model (nil)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a742b0 (Rating)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [songs_view_sort_order_changed_cb] rb-browser-source.c:649: sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a743b0 (Last Played)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [songs_view_sort_order_changed_cb] rb-browser-source.c:649: sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a744b0 (Date Added)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Artist:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [songs_view_sort_order_changed_cb] rb-browser-source.c:649: sort order changed
(13:57:41) [0x8617408] [rb_sourcelist_append] rb-sourcelist.c:1128: inserting source 0x886f170 to group library
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c15a0 chaining to base model (nil)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a746b0 (Date)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76000 (Title)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76100 (Feed)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76200 (Time)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76300 (Rating)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76400 (Play Count)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76500 (Last Played)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a76600 (Status)
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1135: Updating EntryView sort order to Title:0
(13:57:41) [0x8617408] [rb_entry_view_sync_sorting] rb-entry-view.c:1146: emitting sort order changed
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1450 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_read_enter] rhythmdb.c:1176: counter: 1
(13:57:41) [0x8617408] [rhythmdb_query_internal] rhythmdb.c:3952: doing query
(13:57:41) [0x8617408] [do_query_recurse] rhythmdb-tree.c:2240: doing recursive query, 1 conjunctions
(13:57:41) [0x8617408] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2023: adding 0 entries
(13:57:41) [0x8617408] [idle_process_update] rhythmdb-query-model.c:1065: inserting 0 rows
(13:57:41) [0x8617408] [rhythmdb_query_internal] rhythmdb.c:3958: completed
(13:57:41) [0x8617408] [rb_podcast_source_state_prefs_sync] rb-podcast-source.c:998: syncing state
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c16f0 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:659: disposing query model 0x86c15a0
(13:57:41) [0x8617408] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:707: finalizing query model 0x86c15a0
(13:57:41) [0x8617408] [rhythmdb_read_enter] rhythmdb.c:1176: counter: 2
(13:57:41) [0x8a7d080] [query_thread_main] rhythmdb.c:3975: entering query thread
(13:57:41) [0x8a7d080] [rhythmdb_query_internal] rhythmdb.c:3952: doing query
(13:57:41) [0x8a7d080] [do_query_recurse] rhythmdb-tree.c:2240: doing recursive query, 1 conjunctions
(13:57:41) [0x8a7d080] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2023: adding 0 entries
(13:57:41) [0x8a7d080] [rhythmdb_query_internal] rhythmdb.c:3958: completed
(13:57:41) [0x8617408] [rb_sourcelist_append] rb-sourcelist.c:1128: inserting source 0x8a77070 to group library
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x86c1760 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x8a83c20 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:659: disposing query model 0x8a83c20
(13:57:41) [0x8617408] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:707: finalizing query model 0x8a83c20
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a7ec10 (Track)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a7ed10 (Title)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a7ee10 (Artist)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a7ef10 (Album)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a8c0c0 (Location)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a8c1c0 (Last Seen)
(13:57:41) [0x8617408] [rb_source_set_property] rb-source.c:623: Setting Missing Files visibility to 0
(13:57:41) [0x8617408] [rb_sourcelist_append] rb-sourcelist.c:1128: inserting source 0x872d120 to group library
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x8a83e50 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_chain] rhythmdb-query-model.c:784: query model 0x8a83ec0 chaining to base model (nil)
(13:57:41) [0x8617408] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:659: disposing query model 0x8a83ec0
(13:57:41) [0x8617408] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:707: finalizing query model 0x8a83ec0
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a8c3c0 (Location)
(13:57:41) [0x8617408] [rb_entry_view_insert_column_custom] rb-entry-view.c:1689: appending column: 0x8a8c4c0 (Error)
(13:57:41) [0x8617408] [rb_source_set_property] rb-source.c:623: Setting Import Errors visibility to 0
(13:57:41) [0x8617408] [rb_sourcelist_append] rb-sourcelist.c:1128: inserting source 0x872d1b0 to group library
(13:57:41) [0x8617408] [rb_find_user_file] rb-file-helpers.c:199: found user dir path for 'playlists.xml': /home/erik/.local/share/rhythmbox/playlists.xml
(13:57:41) [0x8617408] [construct_sources] rb-shell.c:1233: shell: creating playlist manager
(13:57:41) [0x8617408] [construct_sources] rb-shell.c:1245: shell: creating removable media manager
(13:57:41) [0x8617408] [construct_load_ui] rb-shell.c:1267: shell: loading ui
(13:57:41) [0x8617408] [rb_shell_select_source] rb-shell.c:2078: selecting source 0x886f170
(13:57:41) [0x8617408] [rb_shell_clipboard_set_source_internal] rb-shell-clipboard.c:368: selected source 0x886f170
(13:57:41) [0x8617408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:584: syncing clipboard
(13:57:41) [0x8617408] [rebuild_playlist_menu] rb-shell-clipboard.c:1013: rebuilding add-to-playlist menu
(13:57:41) [0x8617408] [rb_shell_player_set_source_internal] rb-shell-player.c:1070: selected source 0x886f170
(13:57:41) [0x8617408] [rb_shell_player_sync_with_selected_source] rb-shell-player.c:3401: syncing with selected source: 0x886f170
(13:57:41) [0x8617408] [rb_shell_player_sync_with_selected_source] rb-shell-player.c:3404: no playing source, new source is 0x886f170
(13:57:41) [0x8617408] [rb_shell_player_sync_with_source] rb-shell-player.c:2938: playing source: (nil), active entry: (nil)
(13:57:41) [0x8617408] [rb_shell_set_window_title] rb-shell.c:2182: clearing title
(13:57:41) [0x8617408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(13:57:41) [0x8617408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(13:57:41) [0x8617408] [rb_header_sync] rb-header.c:460: syncing with entry = <null>
(13:57:41) [0x8617408] [rb_header_sync] rb-header.c:536: not playing
(13:57:41) [0x8617408] [rb_shell_player_sync_buttons] rb-shell-player.c:3041: syncing with source 0x886f170
(13:57:41) [0x8617408] [rb_source_header_set_source_internal] rb-source-header.c:509: selected source 0x886f170
(13:57:41) [0x8617408] [rb_source_header_view_browser_changed_cb] rb-source-header.c:831: got view browser toggle
(13:57:41) [0x8617408] [rb_source_header_view_browser_changed_cb] rb-source-header.c:844: got view browser toggle
(13:57:41) [0x8617408] [rb_statusbar_set_property] rb-statusbar.c:351: selected source 0x886f170
(13:57:41) [0x8617408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '0 songs', '', -1.000000
Segmentation fault
```

UPDATE! Oddly enough, 2 days later, everything works perfectly. In the meantime I transitioned nicely to VLC and Exaile.

---

### Post by geoffree on 2009-11-20
> **hetx said:**
> I looked around for similar problems but I can't seem to weed them out. In my case ONLY the Totem Movie Player crashes, it doesn't matter if I try to play a video with it or just start it using the menu. The window pops up and disappears right away. I can still watch video with VLC but it's bugging me! Grateful for any help!

Ubuntu 9.04
Also Totem Crash.  Running 9.04 on IBM deskset.  Same as you all. Removed restricted mods but no diff.  Removed/reinstalled Totem. No dice.  Wont play DVD or .wmv on hard drive.  Same with Kino.  But...Avidmux does play movies.  But not in the form I like. Its for editing.  I got message about /dev/raw1394 but is not in file list.  Relates to FireWire anyway.  This is not nice.  
Do others run 9.04 or Krimson Koala?  If fixed in 9.1 I gladly upgrade. 
So?

Geoffree

---

### Post by 4Orbs on 2009-11-20
Totem crashes if I have "Load Subtitles Automatically" enabled, but it doesn't crash if that option is not enabled.

---

