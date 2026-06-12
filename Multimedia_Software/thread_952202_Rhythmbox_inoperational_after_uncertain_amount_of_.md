---
title: "Rhythmbox inoperational after uncertain amount of time elapsed"
date: 2008-10-18
forum: Multimedia Software
---

### Post by t3dward on 2008-10-18
I have upgraded from 7.10 to 8.04, and have been experiencing problems with rhythmbox.

After a fresh boot (warm or cold) rhythmbox functions normally, and I can play songs all throughout my library without issue (all mp3's) for more than an hour. If I leave my machine and come back though, rhythmbox will not play a new song. If I double click a track (or select it and press play) it hangs at 0:00. At this point I am still able to use the interface to search for new tracks to play, but if I attempt to select another song, the program halts hard.

I can shut down the program and kill all instances (verfied by ps aux | grep rhythmbox) but when the program is restarted the same issue remains. This can only be cleared up by either rebooting, or killing X and restarting my window session.

Has anyone experienced this before?
```
(20:40:06) [0x80dc408] [window_focus_cb] rb-mmkeys-plugin.c:118: window got focus, re-grabbing media keys
(20:40:10) [0x80dc408] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:745: entryview changed
(20:40:10) [0x80dc408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:543: syncing clipboard
(20:40:10) [0x80dc408] [rb_entry_view_row_activated_cb] rb-entry-view.c:1713: row activated
(20:40:10) [0x80dc408] [rb_entry_view_row_activated_cb] rb-entry-view.c:1717: emitting entry activated
(20:40:10) [0x80dc408] [rb_shell_player_entry_activated_cb] rb-shell-player.c:2377: got entry 0xb37119e0 activated
(20:40:10) [0x80dc408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:2782: setting playing source to 0x826ee30
(20:40:10) [0x80dc408] [rb_shell_player_sync_with_source] rb-shell-player.c:2611: playing source: 0x826ee30, active entry: (nil)
(20:40:10) [0x80dc408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:2995: Did not get playing entry : return -1 as length
(20:40:10) [0x80dc408] [show_controls] rb-visualizer-plugin.c:838: showing controls
(20:40:10) [0x80dc408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:2995: Did not get playing entry : return -1 as length
(20:40:10) [0x80dc408] [rb_header_sync] rb-header.c:355: syncing with entry = (nil)
(20:40:10) [0x80dc408] [rb_header_sync] rb-header.c:431: not playing
(20:40:10) [0x80dc408] [rb_shell_player_sync_buttons] rb-shell-player.c:2716: syncing with source 0x826ee30
(20:40:10) [0x80dc408] [rb_shell_playing_source_changed_cb] rb-shell.c:1937: playing source changed
(20:40:10) [0x80dc408] [create_stream] rb-player-gst-xfade.c:1900: creating new stream for file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3 (stream data 0xb37119e0)
(20:40:10) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:491: current stream list:
(20:40:10) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:513: [waiting] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:10) [0x80dc408] [start_sink] rb-player-gst-xfade.c:2504: starting sink
(20:40:10) [0x8156108] [stream_new_decoded_pad_cb] rb-player-gst-xfade.c:1816: got decoded audio pad for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:10) [0x8c6aee8] [stream_src_blocked_cb] rb-player-gst-xfade.c:2307: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3 is prerolled, not starting yet -> WAITING
(20:40:10) [0x80dc408] [start_sink] rb-player-gst-xfade.c:2534: silence bin is now in state PAUSED
(20:40:10) [0x80dc408] [start_sink] rb-player-gst-xfade.c:2541: adder is now in state PAUSED
(20:40:11) [0x80dc408] [start_sink] rb-player-gst-xfade.c:2548: output bin is now in state PAUSED
(20:40:11) [0x80dc408] [start_sink] rb-player-gst-xfade.c:2568: sink playing
(20:40:11) [0x80dc408] [rb_player_gst_xfade_play] rb-player-gst-xfade.c:3091: playing stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, crossfade -1
(20:40:11) [0x80dc408] [actually_start_stream] rb-player-gst-xfade.c:2166: going to start playback for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3 (crossfade -1) -> FADING_IN | PLAYING
(20:40:11) [0x80dc408] [link_and_unblock_stream] rb-player-gst-xfade.c:1070: linking stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [link_and_unblock_stream] rb-player-gst-xfade.c:1105: now have 1 linked streams
(20:40:11) [0x80dc408] [rb_shell_player_set_playing_entry] rb-shell-player.c:1564: Success!
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag title for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 0 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag artist for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag album for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag date for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag comment for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 5 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag track-number for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag genre for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 4 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag track-count for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag audio-codec for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag bitrate for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 20 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag layer for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag mode for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag emphasis for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag bitrate for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 20 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x8c6aee8] [link_unblocked_cb] rb-player-gst-xfade.c:1031: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3 is unblocked -> FADING_IN | PLAYING
(20:40:11) [0x8c6aee8] [adjust_stream_base_time] rb-player-gst-xfade.c:858: adjusting base time: 185759637 - 52251095 => 133508542
(20:40:11) [0x8c6aee8] [link_unblocked_cb] rb-player-gst-xfade.c:1044: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3 state change returned: SUCCESS
(20:40:11) [0x8c6aee8] [post_stream_playing_message] rb-player-gst-xfade.c:814: posting rb-stream-playing message for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x8c6aee8] [stream_src_event_cb] rb-player-gst-xfade.c:1871: got new segment for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x8c6aee8] [adjust_stream_base_time] rb-player-gst-xfade.c:858: adjusting base time: 185759637 - 52251095 => 133508542
(20:40:11) [0x80dc408] [rb_player_gst_xfade_bus_cb] rb-player-gst-xfade.c:1604: got stream playing message for file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:745: entryview changed
(20:40:11) [0x80dc408] [new_playing_stream_idle_cb] rb-shell-player.c:3088: new playing stream: file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:11) [0x80dc408] [rb_shell_hidden_notify_markup] rb-shell.c:3100: shell is visible, not notifying
(20:40:11) [0x80dc408] [rb_shell_player_sync_with_source] rb-shell-player.c:2611: playing source: 0x826ee30, active entry: 0xb37119e0
(20:40:11) [0x80dc408] [rb_shell_set_window_title] rb-shell.c:2150: setting title to "Stevie Wonder - Superstition"
(20:40:11) [0x80dc408] [show_controls] rb-visualizer-plugin.c:838: showing controls
(20:40:11) [0x80dc408] [rb_header_sync] rb-header.c:355: syncing with entry = 0xb37119e0
(20:40:11) [0x80dc408] [rb_shell_player_sync_buttons] rb-shell-player.c:2716: syncing with source 0x826ee30
(20:40:11) [0x80dc408] [show_controls] rb-visualizer-plugin.c:838: showing controls
(20:40:11) [0x80dc408] [paned_size_allocate_cb] rb-shell.c:2801: paned position 181
(20:40:11) [0x80dc408] [sidebar_paned_size_allocate_cb] rb-shell.c:2811: sidebar paned position 300
(20:40:11) [0x80dc408] [paned_size_allocate_cb] rb-shell.c:2801: paned position 181
(20:40:11) [0x80dc408] [sidebar_paned_size_allocate_cb] rb-shell.c:2811: sidebar paned position 300
(20:40:11) [0x80dc408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:543: syncing clipboard
(20:40:11) [0x80dc408] [rb_shell_player_sync_with_source] rb-shell-player.c:2611: playing source: 0x826ee30, active entry: 0xb37119e0
(20:40:11) [0x80dc408] [show_controls] rb-visualizer-plugin.c:838: showing controls
(20:40:11) [0x80dc408] [rb_header_sync] rb-header.c:355: syncing with entry = 0xb37119e0
(20:40:11) [0x80dc408] [rb_shell_hidden_notify_markup] rb-shell.c:3100: shell is visible, not notifying
(20:40:11) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:11) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:11) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:11) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:12) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:12) [0x80dc408] [inhibit] rb-power-manager-plugin.c:193: inhibiting
(20:40:12) [0x80dc408] [inhibit_cb] rb-power-manager-plugin.c:173: got cookie 2018018439
(20:40:12) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:12) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:12) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:12) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:13) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:13) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:13) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:13) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:13) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:14) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:14) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:14) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:14) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:14) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:15) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:15) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:15) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:15) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:15) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:16) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:16) [0x80dc408] [actually_hide_controls] rb-visualizer-plugin.c:798: hiding controls
(20:40:16) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:16) [0x80dc408] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:745: entryview changed
(20:40:16) [0x80dc408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:543: syncing clipboard
(20:40:16) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:16) [0x80dc408] [rb_entry_view_row_activated_cb] rb-entry-view.c:1713: row activated
(20:40:16) [0x80dc408] [rb_entry_view_row_activated_cb] rb-entry-view.c:1717: emitting entry activated
(20:40:16) [0x80dc408] [rb_shell_player_entry_activated_cb] rb-shell-player.c:2377: got entry 0xb3711020 activated
(20:40:16) [0x80dc408] [create_stream] rb-player-gst-xfade.c:1900: creating new stream for file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3 (stream data 0xb3711020)
(20:40:16) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:491: current stream list:
(20:40:16) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:513: [waiting] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:513: [playing] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:16) [0x80dc408] [rb_player_gst_xfade_play] rb-player-gst-xfade.c:3091: playing stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3, crossfade -1
(20:40:16) [0x80dc408] [rb_player_gst_xfade_play] rb-player-gst-xfade.c:3106: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3 is prerolling; will start playback once prerolling is complete -> PREROLL_PLAY
(20:40:16) [0x80dc408] [rb_shell_player_set_playing_entry] rb-shell-player.c:1564: Success!
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag title for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 0 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag artist for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag album for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag date for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag comment for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 5 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag track-number for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag genre for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 4 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag track-count for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x8de1968] [stream_new_decoded_pad_cb] rb-player-gst-xfade.c:1816: got decoded audio pad for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag audio-codec for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag bitrate for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 20 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag layer for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag mode for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag emphasis for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1379: got tag bitrate for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [process_tag] rb-player-gst-xfade.c:1418: emitting info field 20 for uri file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:745: entryview changed
(20:40:16) [0x80dc408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:543: syncing clipboard
(20:40:16) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3, 0:266(1)]
(20:40:16) [0x8cd0700] [stream_src_blocked_cb] rb-player-gst-xfade.c:2312: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3 is prerolled, need to start it
(20:40:16) [0x8cd0700] [actually_start_stream] rb-player-gst-xfade.c:2166: going to start playback for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3 (crossfade -1) -> FADING_IN | PLAYING
(20:40:16) [0x8cd0700] [actually_start_stream] rb-player-gst-xfade.c:2268: stopping stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3 (replaced by new stream)
(20:40:16) [0x8cd0700] [link_and_unblock_stream] rb-player-gst-xfade.c:1070: linking stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x8cd0700] [link_and_unblock_stream] rb-player-gst-xfade.c:1105: now have 2 linked streams
(20:40:16) [0x8cd0700] [dump_stream_list] rb-player-gst-xfade.c:491: current stream list:
(20:40:16) [0x8cd0700] [dump_stream_list] rb-player-gst-xfade.c:513: [preroll->play] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x8cd0700] [dump_stream_list] rb-player-gst-xfade.c:513: [pending remove] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:16) [0x8cd0700] [link_unblocked_cb] rb-player-gst-xfade.c:1031: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3 is unblocked -> FADING_IN | PLAYING
(20:40:16) [0x8cd0700] [adjust_stream_base_time] rb-player-gst-xfade.c:858: adjusting base time: 348299319 - 26128647 => 322170672
(20:40:16) [0x8cd0700] [link_unblocked_cb] rb-player-gst-xfade.c:1044: stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3 state change returned: SUCCESS
(20:40:16) [0x8cd0700] [post_stream_playing_message] rb-player-gst-xfade.c:814: posting rb-stream-playing message for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x8cd0700] [stream_src_event_cb] rb-player-gst-xfade.c:1871: got new segment for stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x8cd0700] [adjust_stream_base_time] rb-player-gst-xfade.c:858: adjusting base time: 348299319 - 26128647 => 322170672
(20:40:16) [0x80dc408] [rb_player_gst_xfade_bus_cb] rb-player-gst-xfade.c:1604: got stream playing message for file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:491: current stream list:
(20:40:16) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:513: [playing] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_BIG_BROTHER_.MP3
(20:40:16) [0x80dc408] [dump_stream_list] rb-player-gst-xfade.c:513: [pending remove] file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:16) [0x80dc408] [reap_streams] rb-player-gst-xfade.c:1344: reaping stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:16) [0x80dc408] [unlink_and_dispose_stream] rb-player-gst-xfade.c:1285: stopping stream file:///home/teddy/Desktop/TALKING_BOOK/STEVIE_WONDER_SUPERSTITION.MP3
(20:40:45) [0x8061420] [electromagnetic_shotgun] rb-metadata-dbus-service.c:346: shutting down (44s idle)

```

---

### Post by Iowa Dave on 2008-10-19
I ran into a similar problem. I recently upgraded to 8.04. Ogg files which played back fine under 6.06 sound good but... after a while playback hangs in a series of rat-a-tat sound pulses.

I've checked drivers: my hardware is by "via" and the openchrome drivers are installed. I've also followed the directions [from the Forums, here]("http://ubuntuforums.org/showthread.php?t=205449") to check hardware, locate drivers, modprobe them, and reinstall the alsa files. No joy.

This problem appears in Audacity and other audio players as well. It is widely discussed in the buglogs. The developers keep declaring it "closed" but of course it isn't because ordinary folks like you and me continue to encounter it. They also classify it "low" priority on the grounds that it doesn't prevent Ubuntu from running, they have more important things to do, some other team is supposed to be working on it, etc., etc.

This problem apparently strikes only a minority of unlucky users, and randomly at that. (It hits me every time, usually within a minute of starting audio playback.) The engineers, who know how to tweak their systems better than the rest of us, shrug it off with a dismissive "WFM" ("works for me").

Clearly Ubuntu knows about this sound problem with the 8.04 release. 8.04 is a long term support release, so I hope that eventually they will resolve this problem. For the time being, Ubuntu 8.04 is great for lots of things, but not for playing music.

---

### Post by t3dward on 2008-10-19
I'll give it another run, it's just so damn weird because my audio still works. I can listen to you-tube and the hardware test creates a dandy little sound. I'll wait for 8.10 I guess and hope whatever the hell happened has been fixed.

---

### Post by t3dward on 2008-10-19
Thanks for the link to the audio guide, I removed and restored the base packages, and although I had to reinstall gdm and ubuntu-desktop, my volume is back to what it was in the 7.10 days. We'll see tomorrow if it fixed the issue described above.

---

### Post by Iowa Dave on 2008-10-26
The Ubuntu installer's default audio settings might need a tweak. That would be under System > Preferences > Sound. My Sound Preferences dialog (version 8.04 LTS) wants me to choose separate playback schemes for "sound events", music and movies, audio conferencing, and default mixer tracks. I found these set to "Autodetect" following the Ubuntu installation. One exception, the default mixer tracks were set to "HDA VIA 82xx".

I changed them to the actual coder-decoder ("Codec") hardware built into my motherboard, which in my case is "ALC833." The choice was right there, on the short list of playback options offered by Ubuntu. I found the information about my Codec in the specifications sheet that came with the computer. Putting 2 and 2 together...

The motherboard has both a VIA 82-something chipset and the ALC833 audio coder/decoder. This made it confusing because Ubuntu offered me both of those choices for some playback preferences. Hey, if it confused me, then maybe it was confusing the "Autodetect" algorithm of the system sound preferences as well. Maybe the two were fighting one another for control of my music. 

I set all of the playback elections to be the same, the ALC833 Codec. It is too early to say for sure if this cured my computer of its erratic sound production, but it seems to have done. I will post back here after letting it play for a day or two. 

Point is, sometimes the problem is simpler than we like to think. Instead of being a deep, mysterious kernel or driver problem, maybe it's as simple as setting preferences. I hope this information helps somebody, and I hope that the Ubuntu community will continue to help people by offering simple suggestions like this.

Iowa Dave

---

### Post by Iowa Dave on 2008-10-26
I cured my sound problem by adjusting the settings in System > Preferences > Sound after installing Ubuntu 8.04. "Autodetect" was set by default. What I did was to select the setting for my actual audio hardware. See previous post.

---

