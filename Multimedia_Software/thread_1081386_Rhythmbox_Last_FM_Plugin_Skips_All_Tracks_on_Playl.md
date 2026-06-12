---
title: "Rhythmbox Last FM Plugin Skips All Tracks on Playlist"
date: 2009-02-26
forum: Multimedia Software
---

### Post by pennstatebadboy on 2009-02-26
The LastFM plugin for Rhythmbox is no longer working properly. The playlists load, but the tracks keep advancing in rapid order leaving a red circle with a minus sign next to the track. This goes on and on cycling through the playlist while adding new songs to the playlist.

I tried another LastFM client BMPx and the same thing happens. The tracks cycle through rapidly, but never play. This leads me to believe that there's something wrong with my system or with LastFM.

Any idea what's going on?

---

### Post by thtrgremlin on 2009-02-26
Well, there are ways to rule things out, each with various levels of difficulty. Some simple things to check:
Can you play other media from your hard drive?
Can you play streaming media from other sites?
Can you play locally hosted streaming media? (ok, that might takr a little setup depending on what you do already)
Can you grab the media off the site with another application?
Is the web site up?
If you are getting track names, but not the actual media, check for network errors with an application like wireshark to see where the real network error is.
If in case your preferences are corrupted, you may be able to delete a profile from your home directory which would be rebuilt by running rhythembox again
use synaptic to do a 'complete removal' (not just a normal remove), and reinstall in case the application is avually corrupted for some odd reason.
Was rhythmbox updated recently?
Run rhythmbox from a command line and see if there is any debugging output.

the red circle with the slash basically means it couldn't play the media, either because it was corrupted or because it could not get it. It skips assuming it was just the one file, and that you want to get moving along to music rather than error messages. Oh, and there may be an error slog giving more specific information. The fact that all the medai failed just wasn't something the application views as a special circumstance, i'd bet.

---

### Post by pennstatebadboy on 2009-02-26
Well, there are ways to rule things out, each with various levels of difficulty. Some simple things to check:

*Can you play other media from your hard drive?*
   Yes.

*Can you play streaming media from other sites?*
   Yes.

*Can you play locally hosted streaming media? (ok, that might takr a little setup depending on what you do already)*
   I don't know. Why would I want to stream local media?

*Can you grab the media off the site with another application?*
   LastFM works if I go to its Web site and use its Web player. But I cannot get other applications to play content. For example, BMPx will find songs, but not play them--just like Rhythmbox.

*Is the web site up?*
   Yes.

*If you are getting track names, but not the actual media, check for network errors with an application like wireshark to see where the real network error is.*
   I'm not sure how to do this.

*If in case your preferences are corrupted, you may be able to delete a profile from your home directory which would be rebuilt by running rhythembox again use synaptic to do a 'complete removal' (not just a normal remove), and reinstall in case the application is avually corrupted for some odd reason.*
  I tried that with no success.

*Was rhythmbox updated recently?*
   No.
[I]
Run rhythmbox from a command line and see if there is any debugging output.[/I]
```
(15:54:07) [0x9b9f408] [media_player_key_pressed] rb-mmkeys-plugin.c:103: got media key 'Play' for application 'Rhythmbox'

(15:54:07) [0x9b9f408] [rb_shell_player_playpause] rb-shell-player.c:2336: doing playpause

(15:54:07) [0x9b9f408] [rb_shell_player_playpause] rb-shell-player.c:2367: no playing source, using selected source

(15:54:07) [0x9b9f408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3120: setting playing source to 0xa417000

(15:54:07) [0x9b9f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: 0xa417000, active entry: 0xa80a968

(15:54:07) [0x9b9f408] [rb_shell_set_window_title] rb-shell.c:2164: setting title to "Billy Strange - 007 Theme"

(15:54:07) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:07) [0x9b9f408] [rb_header_sync] rb-header.c:452: syncing with entry = [http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3](http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3)

(15:54:07) [0x9b9f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0xa417000

(15:54:07) [0x9b9f408] [rb_shell_playing_source_changed_cb] rb-shell.c:1951: playing source changed

(15:54:07) [0x9b9f408] [rb_player_gst_sync_pipeline] rb-player-gst.c:718: syncing pipeline

(15:54:07) [0x9b9f408] [rb_player_gst_sync_pipeline] rb-player-gst.c:720: PLAYING pipeline



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_ref: assertion `entry != NULL' failed

(15:54:07) [0x9b9f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: 0xa417000, active entry: 0xa80a968

(15:54:07) [0x9b9f408] [rb_shell_set_window_title] rb-shell.c:2164: setting title to "Billy Strange - 007 Theme"

(15:54:07) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:07) [0x9b9f408] [rb_header_sync] rb-header.c:452: syncing with entry = [http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3](http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3)

(15:54:07) [0x9b9f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0xa417000

(15:54:07) [0x9b9f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: 0xa417000, active entry: 0xa80a968

(15:54:07) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:07) [0x9b9f408] [rb_header_sync] rb-header.c:452: syncing with entry = [http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3](http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3)

(15:54:07) [0x9b9f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0xa417000

(15:54:07) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:07) [0x9b9f408] [LocalCoverArtSearch.search] /usr/lib/rhythmbox/plugins/artdisplay/LocalCoverArtSearch.py:138: not searching for local art for [http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3](http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3)



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:07) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]

(15:54:07) [0x9b9f408] [rb_shell_player_error] rb-shell-player.c:3421: playback error while playing: "http://kingpin6.last.fm/user/a8da46f6286bdce26c91c280dcb98551.mp3": Invalid ticket

(15:54:07) [0x9b9f408] [error_cb] rb-shell-player.c:3574: exiting error hander

(15:54:07) [0x9b9f408] [rb_shell_player_error] rb-shell-player.c:3421: playback error while playing: Stream contains no data.

(15:54:07) [0x9b9f408] [error_cb] rb-shell-player.c:3574: exiting error hander

(15:54:07) [0x9b9f408] [rb_shell_player_handle_eos] rb-shell-player.c:924: called to simulate EOS for playing entry, but nothing is playing

(15:54:07) [0x9b9f408] [rhythmdb_read_enter] rhythmdb.c:1052: counter: 1

(15:54:07) [0x9b9f408] [rhythmdb_read_enter] rhythmdb.c:1052: counter: 2

(15:54:07) [0xa833bd8] [query_thread_main] rhythmdb.c:3800: entering query thread

(15:54:07) [0xa833bd8] [rhythmdb_query_internal] rhythmdb.c:3777: doing query

(15:54:07) [0xa833bd8] [do_query_recurse] rhythmdb-tree.c:2237: doing recursive query, 1 conjunctions

(15:54:07) [0xa833bd8] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2023: adding 0 entries

(15:54:07) [0xa833bd8] [rhythmdb_query_internal] rhythmdb.c:3783: completed

(15:54:07) [0xac484a0] [query_thread_main] rhythmdb.c:3800: entering query thread

(15:54:07) [0x9b9f408] [idle_process_update] rhythmdb-query-model.c:1065: inserting 0 rows

(15:54:07) [0xac484a0] [rhythmdb_query_internal] rhythmdb.c:3777: doing query

(15:54:07) [0xac484a0] [do_query_recurse] rhythmdb-tree.c:2237: doing recursive query, 1 conjunctions

(15:54:07) [0x9b9f408] [rhythmdb_process_one_event] rhythmdb.c:2347: processing RHYTHMDB_EVENT_QUERY_COMPLETE

(15:54:07) [0x9b9f408] [rhythmdb_read_leave] rhythmdb.c:1066: counter: 1

(15:54:07) [0x9b9f408] [rhythmdb_idle_save] rhythmdb.c:4646: database is dirty, doing regular save

(15:54:07) [0x9b9f408] [rhythmdb_save_async] rhythmdb.c:3011: saving the rhythmdb in the background

(15:54:07) [0x9b9f408] [rhythmdb_read_enter] rhythmdb.c:1052: counter: 2

(15:54:07) [0xac484a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2023: adding 0 entries

(15:54:07) [0xac484a0] [rhythmdb_query_internal] rhythmdb.c:3783: completed

(15:54:07) [0xabf00c8] [rhythmdb_save_thread_main] rhythmdb.c:2959: entering save thread

(15:54:07) [0xabf00c8] [rhythmdb_save_thread_main] rhythmdb.c:2977: saving rhythmdb

(15:54:07) [0xabf00c8] [save_entry_type] rhythmdb-tree.c:1127: saving entries of type song

(15:54:07) [0xabf00c8] [save_entry_type] rhythmdb-tree.c:1127: saving entries of type ignore

(15:54:07) [0xabf00c8] [save_entry_type] rhythmdb-tree.c:1127: saving entries of type podcast-feed

(15:54:07) [0xabf00c8] [save_entry_type] rhythmdb-tree.c:1127: saving entries of type iradio

(15:54:07) [0xabf00c8] [save_entry_type] rhythmdb-tree.c:1127: saving entries of type podcast-post

(15:54:07) [0xabf00c8] [save_entry_type] rhythmdb-tree.c:1127: saving entries of type lastfm-station

(15:54:07) [0x9b9f408] [idle_process_update] rhythmdb-query-model.c:1065: inserting 0 rows

(15:54:07) [0x9b9f408] [rhythmdb_process_one_event] rhythmdb.c:2340: processing RHYTHMDB_EVENT_THREAD_EXITED

(15:54:07) [0x9b9f408] [rhythmdb_process_one_event] rhythmdb.c:2347: processing RHYTHMDB_EVENT_QUERY_COMPLETE

(15:54:07) [0x9b9f408] [rhythmdb_read_leave] rhythmdb.c:1066: counter: 1

(15:54:07) [0x9b9f408] [rhythmdb_process_one_event] rhythmdb.c:2340: processing RHYTHMDB_EVENT_THREAD_EXITED

(15:54:07) [0x9b9f408] [rhythmdb_process_one_event] rhythmdb.c:2343: processing RHYTHMDB_EVENT_DB_SAVED

(15:54:07) [0x9b9f408] [rhythmdb_read_leave] rhythmdb.c:1066: counter: 0

(15:54:07) [0x9b9f408] [rhythmdb_process_one_event] rhythmdb.c:2340: processing RHYTHMDB_EVENT_THREAD_EXITED



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:07) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:07) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:08) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:08) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:08) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:08) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:08) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:09) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed



(rhythmbox:15122): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(15:54:09) [0x9b9f408] [tick_cb] rb-shell-player.c:3613: tick: [(null), 4294967295:0(0)]

(15:54:09) [0x9b9f408] [media_player_key_pressed] rb-mmkeys-plugin.c:103: got media key 'Stop' for application 'Rhythmbox'

(15:54:09) [0x9b9f408] [rb_shell_player_stop] rb-shell-player.c:3184: stopping

(15:54:09) [0x9b9f408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3120: setting playing source to (nil)

(15:54:09) [0x9b9f408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3143: source is already playing, stopping it

(15:54:09) [0x9b9f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: (nil), active entry: (nil)

(15:54:09) [0x9b9f408] [rb_shell_set_window_title] rb-shell.c:2141: clearing title

(15:54:09) [0x9b9f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length

(15:54:09) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:09) [0x9b9f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length

(15:54:09) [0x9b9f408] [rb_header_sync] rb-header.c:452: syncing with entry = <null>

(15:54:09) [0x9b9f408] [rb_header_sync] rb-header.c:528: not playing

(15:54:09) [0x9b9f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0xa417000

(15:54:09) [0x9b9f408] [rb_shell_playing_source_changed_cb] rb-shell.c:1951: playing source changed

(15:54:09) [0x9b9f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: (nil), active entry: (nil)

(15:54:09) [0x9b9f408] [rb_shell_set_window_title] rb-shell.c:2141: clearing title

(15:54:09) [0x9b9f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length

(15:54:09) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:09) [0x9b9f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length

(15:54:09) [0x9b9f408] [rb_header_sync] rb-header.c:452: syncing with entry = <null>

(15:54:09) [0x9b9f408] [rb_header_sync] rb-header.c:528: not playing

(15:54:09) [0x9b9f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length

(15:54:09) [0x9b9f408] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1290: called with no playing entry

(15:54:09) [0x9b9f408] [show_controls] rb-visualizer-plugin.c:846: showing controls

(15:54:09) [0x9b9f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0xa417000

(15:54:14) [0x9b9f408] [actually_hide_controls] rb-visualizer-plugin.c:806: hiding controls
```

---

### Post by talent03 on 2009-02-26
I have the same problem. It was working just fine before, but one interesting thing happened yesterday. At one moment rhythmbox gave me a note that appeared to be comming from last.fm. It said that the streaming service is going through maintence. Other than that time, it just goes through every song and skips it.

---

### Post by yauhen on 2009-02-26
Tried LAST FM through Rhythmbox for the first time. After playing one song keeps cycling the same way

---

### Post by snl2587 on 2009-02-26
I had this same problem while back and couldn't find a solution...but since then I've happily switched over to Amarok (although it has its own share of issues with switching stations at the moment..namely that it doesn't always work the first time).

My advice? Use the web client for streaming the stations or get the .deb for the Last.fm client software from [http://apt.last.fm/](http://apt.last.fm/) (don't know if they changed this recently, but last I checked it choked on Pulseaudio). Hopefully this issue will be corrected in the future.

---

### Post by pennstatebadboy on 2009-02-27
Thanks for the responses. If anyone has success getting things to work again, please post your workaround.

---

