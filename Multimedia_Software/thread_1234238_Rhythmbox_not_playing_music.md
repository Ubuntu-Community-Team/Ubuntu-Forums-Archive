---
title: "Rhythmbox not playing music"
date: 2009-08-07
forum: Multimedia Software
---

### Post by satbunny on 2009-08-07
I have some mp3s. They play fine if I hover over them in Nautilus with the mouse. They play fine in Totem. I have all the extra codecs installed a la Medibuntu and the FAQ on this forum.

But Rhythmbox just fails on every file in my library.

I am running Ubuntu 9.04 2.6.28-14-generic, Ubuntu Netbook Remix, on a Dell Mini 12, with Rhythmbox 0.12.0

I have the output of Rhythmbox run in debug mode but it's too big to upload.

---

### Post by satbunny on 2009-08-07
Oddly the only error message I can find is:

(21:03:02) [0x961a408] [rb_shell_player_error] rb-shell-player.c:3423: playback error while playing: Failed to create output image buffer of 60x60 pixels

---

### Post by satbunny on 2009-08-07
Okay.. looks like it is a very deep seated bug with gstreamer related, amazingly, to the video driver (the dreaded poulsbo driver in my case) as reported here..

I think I'll just try Songbird..  wonder if that will fail?

---

### Post by pulpi on 2009-10-25
Same problem with ubuntu 9.04. Rhythmbox version is 0.12.0. Sometimes it plays and sometimes I get error.

```
(19:20:41) [0x994f408] [rb_shell_window_configure_cb] rb-shell.c:1635: storing window size of 711:397
(19:20:41) [0x994f408] [rb_shell_window_configure_cb] rb-shell.c:1647: storing window position of 623:25
(19:20:41) [0x994f408] [window_focus_cb] rb-mmkeys-plugin.c:142: window got focus, re-grabbing media keys
(19:20:43) [0x994f408] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:786: entryview changed
(19:20:43) [0x994f408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:584: syncing clipboard
(19:20:43) [0x994f408] [rb_entry_view_row_activated_cb] rb-entry-view.c:2073: row activated
(19:20:43) [0x994f408] [rb_entry_view_row_activated_cb] rb-entry-view.c:2077: emitting entry activated
(19:20:43) [0x994f408] [rb_shell_player_entry_activated_cb] rb-shell-player.c:2703: got entry 0xa447a00 activated
(19:20:43) [0x994f408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3122: setting playing source to 0x9ddeb50
(19:20:43) [0x994f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2938: playing source: 0x9ddeb50, active entry: (nil)
(19:20:43) [0x994f408] [get_times_and_stream] rb-player-gst-xfade.c:2669: not playing
(19:20:43) [0x994f408] [rb_shell_set_window_title] rb-shell.c:2182: clearing title
(19:20:43) [0x994f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:43) [0x994f408] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:43) [0x994f408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:43) [0x994f408] [rb_header_sync] rb-header.c:460: syncing with entry = <null>
(19:20:43) [0x994f408] [rb_header_sync] rb-header.c:536: not playing
(19:20:43) [0x994f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3041: syncing with source 0x9ddeb50
(19:20:43) [0x994f408] [rb_shell_playing_source_changed_cb] rb-shell.c:1992: playing source changed
(19:20:43) [0x994f408] [playing_source_changed_cb] rb-iradio-source.c:1165: connecting info-available signal handler
(19:20:43) [0x994f408] [rb_shell_player_set_playing_entry] rb-shell-player.c:1727: Success!
(19:20:43) [0x994f408] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:786: entryview changed
(19:20:43) [0x994f408] [rb_shell_clipboard_sync] rb-shell-clipboard.c:584: syncing clipboard
(19:20:44) [0x9c49368] [open_location_thread] rb-shell-player.c:1541: playlist parser failed, playing http://72.26.204.18:6716 directly
(19:20:44) [0x9c49368] [rb_shell_player_open_playlist_url] rb-shell-player.c:755: playing stream url http://72.26.204.18:6716
(19:20:44) [0x9c49368] [create_stream] rb-player-gst-xfade.c:2044: creating new stream for http://72.26.204.18:6716 (stream data 0xa447a00)
(19:20:44) [0x9c49368] [dump_stream_list] rb-player-gst-xfade.c:508: current stream list:
(19:20:44) [0x9c49368] [dump_stream_list] rb-player-gst-xfade.c:531: [waiting] http://72.26.204.18:6716
(19:20:44) [0xb4d46150] [stream_queue_underrun_cb] rb-player-gst-xfade.c:1872: http://72.26.204.18:6716: queue underrun
(19:20:44) [0xb4d46150] [post_stream_playing_message] rb-player-gst-xfade.c:832: posting rb-stream-playing message for stream http://72.26.204.18:6716
(19:20:44) [0x994f408] [rb_player_gst_xfade_bus_cb] rb-player-gst-xfade.c:1711: got stream playing message for http://72.26.204.18:6716
(19:20:44) [0x994f408] [new_playing_stream_idle_cb] rb-shell-player.c:3480: new playing stream: http://72.26.204.18:6716
(19:20:44) [0x994f408] [rb_shell_hidden_notify_markup] rb-shell.c:3162: shell is visible, not notifying
(19:20:44) [0x9c49368] [start_sink_locked] rb-player-gst-xfade.c:2727: starting sink
(19:20:44) [0x994f408] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1292: new entry: http://72.26.204.18:6716
(19:20:44) [0x994f408] [get_times_and_stream] rb-player-gst-xfade.c:2608: found buffering stream http://72.26.204.18:6716 as current
(19:20:44) [0x994f408] [rb_audioscrobbler_is_queueable] rb-audioscrobbler.c:485: entry http://72.26.204.18:6716 is not queueable: category not NORMAL
(19:20:44) [0x994f408] [playing_entry_changed_cb] rb-streaming-source.c:468: playing new stream; resetting buffering
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_shell_player_sync_with_source] rb-shell-player.c:2938: playing source: 0x9ddeb50, active entry: 0xa447a00
(19:20:44) [0x994f408] [get_times_and_stream] rb-player-gst-xfade.c:2608: found buffering stream http://72.26.204.18:6716 as current
(19:20:44) [0x994f408] [rb_shell_set_window_title] rb-shell.c:2205: setting title to "SKY.fm - Uptempo Smooth Jazz"
(19:20:44) [0x994f408] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:44) [0x994f408] [rb_header_sync] rb-header.c:460: syncing with entry = http://72.26.204.18:6716
(19:20:44) [0x994f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3041: syncing with source 0x9ddeb50
(19:20:44) [0x994f408] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1057;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077;', 0.000000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 0; threshold 70656 - 0%
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 1198; threshold 70656 - 1%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.010000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 2638; threshold 70656 - 3%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.030000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 4078; threshold 70656 - 5%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.050000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 5518; threshold 70656 - 7%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.070000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 6958; threshold 70656 - 9%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.090000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 8398; threshold 70656 - 11%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.110000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 9838; threshold 70656 - 13%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.130000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 11278; threshold 70656 - 15%
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 12718; threshold 70656 - 17%
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 14158; threshold 70656 - 19%
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 15598; threshold 70656 - 21%
(19:20:44) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:44) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.210000
(19:20:44) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 17038; threshold 70656 - 23%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 18478; threshold 70656 - 25%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 19918; threshold 70656 - 27%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 21358; threshold 70656 - 29%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 22798; threshold 70656 - 31%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 24238; threshold 70656 - 33%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 25678; threshold 70656 - 35%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 27118; threshold 70656 - 37%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 28558; threshold 70656 - 40%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 29998; threshold 70656 - 42%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 31438; threshold 70656 - 44%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.440000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 32878; threshold 70656 - 46%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.460000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 34318; threshold 70656 - 48%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 35758; threshold 70656 - 50%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.500000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 37198; threshold 70656 - 52%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 38638; threshold 70656 - 54%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 40078; threshold 70656 - 56%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 41028; threshold 70656 - 57%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 42468; threshold 70656 - 59%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.590000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 43908; threshold 70656 - 61%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 45348; threshold 70656 - 63%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.630000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 46788; threshold 70656 - 65%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.650000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 48228; threshold 70656 - 67%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 49668; threshold 70656 - 69%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 51108; threshold 70656 - 71%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.710000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 52548; threshold 70656 - 73%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.730000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 53988; threshold 70656 - 75%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 55428; threshold 70656 - 77%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 56868; threshold 70656 - 79%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 58308; threshold 70656 - 81%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 59748; threshold 70656 - 83%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 61188; threshold 70656 - 85%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 62628; threshold 70656 - 87%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 64068; threshold 70656 - 89%
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 65508; threshold 70656 - 91%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.910000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 66948; threshold 70656 - 93%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.930000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 68388; threshold 70656 - 95%
(19:20:45) [0x994f408] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:45) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '&#1041;&#1091;&#1092;&#1077;&#1088;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103;', 0.950000
(19:20:45) [0xb4d20218] [stream_queue_probe_cb] rb-player-gst-xfade.c:1839: http://72.26.204.18:6716: buffer level: 69828; threshold 70656 - 97%
(19:20:45) [0xb4d46150] [stream_queue_threshold_cb] rb-player-gst-xfade.c:1851: http://72.26.204.18:6716: queue running
(19:20:45) [0xb4d46150] [stream_new_decoded_pad_cb] rb-player-gst-xfade.c:1925: got decoded audio pad for stream http://72.26.204.18:6716
(19:20:45) [0xb4d46150] [stream_src_blocked_cb] rb-player-gst-xfade.c:2499: stream http://72.26.204.18:6716 is prerolled, not starting yet -> WAITING
(19:20:45) [0xb4d60360] [stream_src_blocked_cb] rb-player-gst-xfade.c:2485: stream http://72.26.204.18:6716 already blocked
(19:20:49) [0x994f408] [actually_hide_controls] rb-visualizer-plugin.c:804: hiding controls
(19:20:50) [0x9c49368] [start_sink_locked] rb-player-gst-xfade.c:2765: sink is taking too long to start..
(19:20:50) [0x9c49368] [process_tag] rb-player-gst-xfade.c:1487: got tag organization for stream http://72.26.204.18:6716
(19:20:50) [0x9c49368] [process_tag] rb-player-gst-xfade.c:1487: got tag genre for stream http://72.26.204.18:6716
(19:20:50) [0x9c49368] [process_tag] rb-player-gst-xfade.c:1526: emitting info field 4 for uri http://72.26.204.18:6716
(19:20:50) [0x9c49368] [info_available_cb] rb-iradio-source.c:1099: iradio station already has genre: Uptempo Smooth Jazz; ignoring Uptempo Smooth Jazz
(19:20:50) [0x9c49368] [process_tag] rb-player-gst-xfade.c:1487: got tag location for stream http://72.26.204.18:6716
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [process_tag] rb-player-gst-xfade.c:1487: got tag audio-codec for stream http://72.26.204.18:6716
(19:20:50) [0x9c49368] [process_tag] rb-player-gst-xfade.c:1487: got tag audio-codec for stream http://72.26.204.18:6716
(19:20:50) [0x9c49368] [rb_shell_player_error] rb-shell-player.c:3423: playback error while playing: &#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1090;&#1082;&#1088;&#1099;&#1090;&#1100; &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#1074;&#1099;&#1074;&#1086;&#1076;&#1072;
(19:20:50) [0x9c49368] [rhythmdb_entry_set] rhythmdb.c:3266: queuing RHYTHMDB_ACTION_ENTRY_SET
(19:20:50) [0x9c49368] [rb_shell_player_stop] rb-shell-player.c:3186: stopping
(19:20:50) [0x9c49368] [unlink_and_dispose_stream] rb-player-gst-xfade.c:1383: stopping stream http://72.26.204.18:6716
(19:20:50) [0x9c49368] [dump_stream_list] rb-player-gst-xfade.c:506: stream list is empty
(19:20:50) [0x9c49368] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3122: setting playing source to (nil)
(19:20:50) [0x9c49368] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3145: source is already playing, stopping it
(19:20:50) [0x9c49368] [rb_shell_player_sync_with_source] rb-shell-player.c:2938: playing source: (nil), active entry: (nil)
(19:20:50) [0x9c49368] [get_times_and_stream] rb-player-gst-xfade.c:2669: not playing
(19:20:50) [0x9c49368] [rb_shell_set_window_title] rb-shell.c:2182: clearing title
(19:20:50) [0x9c49368] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:50) [0x9c49368] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:50) [0x9c49368] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:50) [0x9c49368] [rb_header_sync] rb-header.c:460: syncing with entry = <null>
(19:20:50) [0x9c49368] [rb_header_sync] rb-header.c:536: not playing
(19:20:50) [0x9c49368] [rb_shell_player_sync_buttons] rb-shell-player.c:3041: syncing with source 0x9ddeb50
(19:20:50) [0x9c49368] [rb_shell_playing_source_changed_cb] rb-shell.c:1992: playing source changed
(19:20:50) [0x9c49368] [playing_source_changed_cb] rb-iradio-source.c:1171: disconnecting info-available signal handler
(19:20:50) [0x9c49368] [rb_shell_player_sync_with_source] rb-shell-player.c:2938: playing source: (nil), active entry: (nil)
(19:20:50) [0x9c49368] [get_times_and_stream] rb-player-gst-xfade.c:2669: not playing
(19:20:50) [0x9c49368] [rb_shell_set_window_title] rb-shell.c:2182: clearing title
(19:20:50) [0x9c49368] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:50) [0x9c49368] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:50) [0x9c49368] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:50) [0x9c49368] [rb_header_sync] rb-header.c:460: syncing with entry = <null>
(19:20:50) [0x9c49368] [rb_header_sync] rb-header.c:536: not playing
(19:20:50) [0x9c49368] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3387: Did not get playing entry : return -1 as length
(19:20:50) [0x9c49368] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1289: called with no playing entry
(19:20:50) [0x9c49368] [rhythmdb_entry_set] rhythmdb.c:3266: queuing RHYTHMDB_ACTION_ENTRY_SET
(19:20:50) [0x9c49368] [rhythmdb_entry_set] rhythmdb.c:3266: queuing RHYTHMDB_ACTION_ENTRY_SET
(19:20:50) [0x9c49368] [rb_statusbar_source_status_changed_cb] rb-statusbar.c:570: source status changed
(19:20:50) [0x9c49368] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:50) [0x9c49368] [rb_shell_player_sync_buttons] rb-shell-player.c:3041: syncing with source 0x9ddeb50
(19:20:50) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '', 0.000000
(19:20:50) [0x994f408] [notify_playing_idle] rb-shell-player.c:718: emitting playing notification: 0
(19:20:50) [0x994f408] [show_controls] rb-visualizer-plugin.c:844: showing controls
(19:20:50) [0x994f408] [rb_shell_player_sync_buttons] rb-shell-player.c:3041: syncing with source 0x9ddeb50
(19:20:50) [0x994f408] [rhythmdb_process_one_event] rhythmdb.c:2490: processing RHYTHMDB_EVENT_ENTRY_SET
(19:20:50) [0x994f408] [rhythmdb_process_one_event] rhythmdb.c:2490: processing RHYTHMDB_EVENT_ENTRY_SET
(19:20:50) [0x994f408] [rhythmdb_process_one_event] rhythmdb.c:2490: processing RHYTHMDB_EVENT_ENTRY_SET
(19:20:50) [0x994f408] [rb_statusbar_sync_status] rb-statusbar.c:470: updating status with: '17 &#1089;&#1090;&#1072;&#1085;&#1094;&#1080;&#1081;', '', 0.000000

```

Is there any solution for this bug?

---

### Post by vinutux on 2009-10-25
You can get a new version from getdeb.net **[http://www.getdeb.net/app/Rhythmbox]("http://www.getdeb.net/app/Rhythmbox")**

---

### Post by pulpi on 2009-10-25
> **vinutux said:**
> You can get a new version from getdeb.net **[http://www.getdeb.net/app/Rhythmbox]("http://www.getdeb.net/app/Rhythmbox")**

Thank you! It started working, but I'll test it some more time to be sure the bug is fixed. :)

---

### Post by vinutux on 2009-10-25
> **pulpi said:**
> Thank you! It started working, but I'll test it some more time to be sure the bug is fixed. :)

plz mark thread SOLVED if it is fixed.........

---

### Post by pulpi on 2009-10-27
> **vinutux said:**
> plz mark thread SOLVED if it is fixed.........

I'm not an owner of thread. How can I do it?

---

### Post by vinutux on 2009-10-27
> **pulpi said:**
> I'm not an owner of thread. How can I do it?

Sorry... i think you are owner of this thread.......

---

