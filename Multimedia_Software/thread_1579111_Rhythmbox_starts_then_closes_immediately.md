---
title: "Rhythmbox starts then closes immediately?"
date: 2010-09-21
forum: Multimedia Software
---

### Post by Sepiraph on 2010-09-21
I have this issue with Rhythmbox where if I tried to open it trhough Applications > Sound & Video, the program would start and close almost immediately.

I ran it in CLI & got:
```
rhythmbox
** (rhythmbox:3378): DEBUG: Loading the real store page
** (rhythmbox:3378): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
Segmentation fault
```

So what now, re-install through Synaptic?

---

### Post by gnush on 2010-09-21
How about trying to uninstall the Ubuntu Music Store plugin for Rhythmbox?

```
sudo apt-get remove rhythmbox-ubuntuone-music-store
```

---

### Post by Sepiraph on 2010-09-21
Same error message. :/

---

### Post by gnush on 2010-09-21
> **Sepiraph said:**
> Same error message. :/


Have you tried to run Rhythmbox with the debug option?

```
rhythmbox -d --gst-plugin-spew
*"--gst-plugin-spew" enables verbose plugin loading diagnostics.*


```

---

### Post by Sepiraph on 2010-09-21
> **gnush said:**
> Have you tried to run Rhythmbox with the debug option?

```
rhythmbox -d --gst-plugin-spew
*"--gst-plugin-spew" enables verbose plugin loading diagnostics.*


```

> **gnush said:**
> Have you tried to run Rhythmbox with the debug option?

```
rhythmbox -d --gst-plugin-spew
*"--gst-plugin-spew" enables verbose plugin loading diagnostics.*


```

I tried to re-install rhythmbox in synaptic, still same error.

I tried to use the -d -gst option and generated A LOT of message:

```
 rhythmbox -d 
(13:20:17) [0x1d5b040] [rb_debug_init_match] rb-debug.c:213: Debugging enabled
(13:20:17) [0x1d5b040] [main] main.c:176: initializing Rhythmbox 0.12.8
(13:20:17) [0x1d5b040] [rb_threads_init] rb-util.c:482: GMutex isn't recursive
(13:20:17) [0x1d5b040] [main] main.c:184: going to create DBus object
(13:20:17) [0x1d5b040] [main] main.c:266: Going to create a new shell
(13:20:17) [0x1d5b040] [rb_shell_constructed] rb-shell.c:1488: Constructing shell
(13:20:17) [0x1d5b040] [construct_db] rb-shell.c:1136: creating database object
(13:20:17) [0x1d5b040] [rb_find_user_file] rb-file-helpers.c:251: no existing file for 'rhythmdb.xml', returning user dir path /home/sepiraph/.local/share/rhythmbox/rhythmdb.xml
(13:20:17) [0x1d5b040] [construct_widgets] rb-shell.c:1203: shell: initializing shell services
(13:20:17) [0x1d5b040] [gconf_network_buffer_size_changed] rb-shell-player.c:3834: network buffer size changed
(13:20:17) [0x1d5b040] [rb_header_sync] rb-header.c:487: syncing with entry = <null>
(13:20:17) [0x1d5b040] [rb_header_sync] rb-header.c:549: not playing
(13:20:17) [0x1d5b040] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3104: setting playing source to (nil)
(13:20:17) [0x1d5b040] [rb_shell_player_sync_with_source] rb-shell-player.c:2928: playing source: (nil), active entry: (nil)
(13:20:17) [0x1d5b040] [rb_shell_player_sync_control_state] rb-shell-player.c:2443: syncing control state
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x20f10f0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x20f11b0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x20f10f0
(13:20:17) [0x1d5b040] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x20f10f0
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x20f1270 ()
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x20f13f0 (Track)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x20f14b0 (Title)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x20f1630 (Genre)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2113010 (Artist)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2113190 (Album)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2113310 (Year)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2113490 (Time)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2113610 (Quality)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2115840 (Rating)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x21159c0 (Play Count)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2115b40 (Location)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2115cc0 (Last Played)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2115e40 (Date Added)
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x212b820 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x212b820 chaining to base model 0x20f11b0
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x212ba60 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x212bb20 (Play Queue)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x212ba60
(13:20:17) [0x1d5b040] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x212ba60
(13:20:17) [0x1d5b040] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x1f8c000 to group library
(13:20:17) [0x1d5b040] [rb_shell_constructed] rb-shell.c:1508: shell: adding gconf notification
(13:20:17) [0x1d5b040] [rb_shell_constructed] rb-shell.c:1541: shell: syncing with gconf
(13:20:17) [0x1d5b040] [rb_source_set_property] rb-source.c:624: Setting Play Queue visibility to 1
(13:20:17) [0x1d5b040] [visibility_notify_cb] rb-sourcelist.c:1017: Source visibility changed: Play Queue
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x2148550 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2148610 (Track)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2146810 (Title)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2146990 (Genre)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2146b10 (Artist)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2146c90 (Album)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2146e10 (Year)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2144000 (Time)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2144180 (Quality)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2144300 (Play Count)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2144480 (Location)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_browser_source_state_prefs_sync] rb-browser-source.c:759: syncing state
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x2144600 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(13:20:17) [0x1d5b040] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(13:20:17) [0x1d5b040] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x2148550
(13:20:17) [0x1d5b040] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x2148550
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x21446c0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215d030 (Rating)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [songs_view_sort_order_changed_cb] rb-browser-source.c:623: sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215d1b0 (Last Played)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [songs_view_sort_order_changed_cb] rb-browser-source.c:623: sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215d330 (Date Added)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Artist:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [songs_view_sort_order_changed_cb] rb-browser-source.c:623: sort order changed
(13:20:17) [0x1d5b040] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x1f24220 to group library
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x215f830 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215f8f0 (Date)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215fa70 (Title)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215fbf0 (Feed)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215fd70 (Time)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215fef0 (Rating)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x216b0c0 (Play Count)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x216b240 (Last Played)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x216b3c0 (Status)
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(13:20:17) [0x1d5b040] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x216b6c0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 1
(13:20:17) [0x1d5b040] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(13:20:17) [0x1d5b040] [do_query_recurse] rhythmdb-tree.c:2251: doing recursive query, 1 conjunctions
(13:20:17) [0x1d5b040] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(13:20:17) [0x1d5b040] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(13:20:17) [0x1d5b040] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(13:20:17) [0x1d5b040] [rb_podcast_source_state_prefs_sync] rb-podcast-source.c:989: syncing state
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x2166b00 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x215f830
(13:20:17) [0x1d5b040] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x215f830
(13:20:17) [0x1d5b040] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 2
(13:20:17) [0x214fcd0] [query_thread_main] rhythmdb.c:4149: entering query thread
(13:20:17) [0x214fcd0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(13:20:17) [0x214fcd0] [do_query_recurse] rhythmdb-tree.c:2251: doing recursive query, 1 conjunctions
(13:20:17) [0x214fcd0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(13:20:17) [0x214fcd0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(13:20:17) [0x1d5b040] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x20011b0 to group library
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x2166bc0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x215f830 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x215f830
(13:20:17) [0x1d5b040] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x215f830
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x215f830 (Track)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2166ec0 (Title)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x21820f0 (Artist)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2182270 (Album)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x21823f0 (Location)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2182570 (Last Seen)
(13:20:17) [0x1d5b040] [rb_source_set_property] rb-source.c:624: Setting Missing Files visibility to 0
(13:20:17) [0x1d5b040] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x1f284d0 to group library
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x21826f0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x21711b0 chaining to base model (nil)
(13:20:17) [0x1d5b040] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x21711b0
(13:20:17) [0x1d5b040] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x21711b0
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2171270 (Location)
(13:20:17) [0x1d5b040] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x2171330 (Error)
(13:20:17) [0x1d5b040] [rb_source_set_property] rb-source.c:624: Setting Import Errors visibility to 0
(13:20:17) [0x1d5b040] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x1f285e0 to group library
(13:20:17) [0x1d5b040] [rb_find_user_file] rb-file-helpers.c:251: no existing file for 'playlists.xml', returning user dir path /home/sepiraph/.local/share/rhythmbox/playlists.xml
(13:20:17) [0x1d5b040] [construct_sources] rb-shell.c:1375: shell: creating playlist manager
(13:20:17) [0x1d5b040] [construct_sources] rb-shell.c:1387: shell: creating removable media manager
(13:20:17) [0x1d5b040] [construct_load_ui] rb-shell.c:1409: shell: loading ui
(13:20:17) [0x1d5b040] [rb_shell_select_source] rb-shell.c:2126: selecting source 0x1f24220
(13:20:17) [0x1d5b040] [rb_shell_clipboard_set_source_internal] rb-shell-clipboard.c:354: selected source 0x1f24220
(13:20:17) [0x1d5b040] [rb_shell_clipboard_sync] rb-shell-clipboard.c:600: syncing clipboard
(13:20:17) [0x1d5b040] [rebuild_playlist_menu] rb-shell-clipboard.c:1034: rebuilding add-to-playlist menu
(13:20:17) [0x1d5b040] [rb_shell_player_set_source_internal] rb-shell-player.c:1098: selected source 0x1f24220
(13:20:17) [0x1d5b040] [rb_shell_player_sync_with_selected_source] rb-shell-player.c:3377: syncing with selected source: 0x1f24220
(13:20:17) [0x1d5b040] [rb_shell_player_sync_with_selected_source] rb-shell-player.c:3380: no playing source, new source is 0x1f24220
(13:20:17) [0x1d5b040] [rb_shell_player_sync_with_source] rb-shell-player.c:2928: playing source: (nil), active entry: (nil)
(13:20:17) [0x1d5b040] [rb_shell_set_window_title] rb-shell.c:2178: clearing title
(13:20:17) [0x1d5b040] [rb_shell_player_sync_buttons] rb-shell-player.c:3023: syncing with source 0x1f24220
(13:20:17) [0x1d5b040] [rb_source_header_set_source_internal] rb-source-header.c:501: selected source 0x1f24220
(13:20:17) [0x1d5b040] [rb_source_header_view_browser_changed_cb] rb-source-header.c:836: got view browser toggle
(13:20:17) [0x1d5b040] [rb_source_header_view_browser_changed_cb] rb-source-header.c:849: got view browser toggle
(13:20:17) [0x1d5b040] [rb_statusbar_set_property] rb-statusbar.c:325: selected source 0x1f24220
(13:20:17) [0x1d5b040] [rb_statusbar_sync_status] rb-statusbar.c:444: updating status with: '0 songs', '', -1.000000

```

---

### Post by war59312 on 2011-01-13
Same here.

The upgrade to Ubuntu 10.10 from 10.04 broke it. :(

> will@will-linux-laptop:~$ rhythmbox

(rhythmbox:7301): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:7301): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:7301): DEBUG: Loading the real store page

** (rhythmbox:7301): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:7301): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
Segmentation fault

---

### Post by war59312 on 2011-02-11
Bump. No ideas?

---

### Post by xtremethegreat1 on 2011-02-12
Try to uninstall and then check your repositories from synaptic. Delete any 10.04 repositories and add maverick repositories. And then reload the packages and install rhythmbox. See if that works.

---

### Post by war59312 on 2011-02-13
Yea tried that, no luck. Looks like something was broken in Ubuntu 10.10.

---

### Post by war59312 on 2011-02-24
Updated to Rhythmbox Version 0.13.1-0ubuntu6.1 and still crashing. :(

---

### Post by buckmaster60 on 2011-04-17
I have the exact same error.  However, my Ubuntu 10.10 is a clean install, no upgrade.  Still looking for an answer.

---

### Post by Yellow Pasque on 2011-04-17
If it's a segmentation fault, you should probably install rhythmbox and gstreamer debugging symbols, and then use gdb to run rhythmbox. That way, you get a backtrace, which is required for filing an effective segfault bug (and/or gives you a specific error message to google).

---

