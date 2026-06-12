---
title: "Rhythmbox won't play after a while"
date: 2009-05-17
forum: Multimedia Software
---

### Post by Volt9000 on 2009-05-17
For some reason, after a while of uptime when I start Rhythmbox it won't play my music. When I click the Play button it will just freeze up and turn dark, forcing me to terminate it. The only fix for this seems to be to restart Ubuntu.

Interestingly enough, playing through VLC still works, as does using SoX's play from the command-line.

Does anyone have any ideas? I've got an Audigy 2 ZS which, otherwise, works perfectly fine.

---

### Post by Volt9000 on 2009-05-18
*bump*
Anyone? This is really annoying me.

---

### Post by kostkon on 2009-05-19
For a start, try running it from the terminal and see if it will print any error messages, i.e. like this:
```
rhythmbox
```
You can also run it in debug mode:
```
rhythmbox -d
```
although it will create a lot of output. But, you can pipe it to a text file, for example, like this:
```
rhythmbox -d | ~/rhythmbox_out.txt
```
whereas *~/* means your home folder.

Hope that helps.

---

### Post by ninjapirate89 on 2009-05-19
I know it's not a fix for Rhythmbox, but have you given Banshee a try? IMHO it superior to Rhythmbox.

---

### Post by Volt9000 on 2009-05-19
I'll give both suggestions a try, thanks guys!

---

### Post by Volt9000 on 2009-05-22
Ok so I tried running Rhythmbox in debug mode and Banshee as well.

For the record, the command to pipe the debug output to a text file is actually:

```

rhythmbox -d 2> ~/rhythmbox_out.txt

```

since the debug code is being output to stderr and not stdout, so that's why the 2> is necessary.

I perused the debug output and found the following relevant lines:

```

(20:49:21) [0x8adc408] [rb_shell_player_cmd_play] rb-shell-player.c:2307: play!
(20:49:21) [0x8adc408] [rb_shell_player_playpause] rb-shell-player.c:2336: doing playpause
(20:49:21) [0x8adc408] [rb_shell_player_playpause] rb-shell-player.c:2367: no playing source, using selected source
(20:49:21) [0x8adc408] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3120: setting playing source to 0x8cf8e00
(20:49:21) [0x8adc408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: 0x8cf8e00, active entry: (nil)
(20:49:21) [0x8adc408] [rb_shell_set_window_title] rb-shell.c:2141: clearing title
(20:49:21) [0x8adc408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length
(20:49:21) [0x8adc408] [show_controls] rb-visualizer-plugin.c:846: showing controls
(20:49:21) [0x8adc408] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3385: Did not get playing entry : return -1 as length
(20:49:21) [0x8adc408] [rb_header_sync] rb-header.c:452: syncing with entry = <null>
(20:49:21) [0x8adc408] [rb_header_sync] rb-header.c:528: not playing
(20:49:21) [0x8adc408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0x8cf8e00
(20:49:21) [0x8adc408] [rb_shell_playing_source_changed_cb] rb-shell.c:1951: playing source changed
(20:49:21) [0x8adc408] [rb_shell_player_playpause] rb-shell-player.c:2405: getting entry from play order
(20:49:21) [0x8adc408] [rb_shuffle_play_order_get_next] rb-play-order-shuffle.c:206: choosing current entry in shuffle
(20:49:21) [0x8adc408] [rb_player_gst_construct] rb-player-gst.c:587: constructing element "playbin"
(20:49:21) [0x8adc408] [mutate_playbin] rb-visualizer-plugin.c:1240: mutating playbin
(20:49:21) [0x8adc408] [find_xoverlay] rb-visualizer-plugin.c:394: found xoverlay in video bin
(20:49:21) [0x8adc408] [fixate_vis_caps] rb-visualizer-plugin.c:486: fixating caps towards 60x60, 1/1
(20:49:21) [0x8adc408] [fixate_vis_caps] rb-visualizer-plugin.c:497: setting fixed caps on capsfilter: video/x-raw-rgb, bpp=(int)32, depth=(int)24, endianness=(int)4321, red_mask=(int)65280, green_mask=(int)16711680, blue_mask=(int)-16777216, width=(int)60, height=(int)60, framerate=(fraction)1/1
(20:49:21) [0x8adc408] [rb_player_gst_construct] rb-player-gst.c:689: pipeline construction complete
(20:49:21) [0x8adc408] [rb_player_gst_sync_pipeline] rb-player-gst.c:718: syncing pipeline
(20:49:21) [0x8adc408] [rb_player_gst_sync_pipeline] rb-player-gst.c:725: PAUSING pipeline
(20:49:21) [0x8adc408] [rb_player_gst_sync_pipeline] rb-player-gst.c:718: syncing pipeline
(20:49:21) [0x8adc408] [rb_player_gst_sync_pipeline] rb-player-gst.c:720: PLAYING pipeline
(20:49:21) [0x8adc408] [rb_shell_player_set_playing_entry] rb-shell-player.c:1733: Success!
(20:49:21) [0x8adc408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: 0x8cf8e00, active entry: 0xb55ba2e0
(20:49:21) [0x8adc408] [rb_shell_set_window_title] rb-shell.c:2164: setting title to "(song title here)"
(20:49:21) [0x8adc408] [show_controls] rb-visualizer-plugin.c:846: showing controls
(20:49:21) [0x8adc408] [rb_header_sync] rb-header.c:452: syncing with entry = (full path to mp3 file here)
(20:49:21) [0x8adc408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0x8cf8e00
(20:49:21) [0x8adc408] [new_playing_stream_idle_cb] rb-shell-player.c:3478: new playing stream: (full path to mp3 file here)
(20:49:21) [0x8adc408] [rb_shell_hidden_notify_markup] rb-shell.c:3121: shell is visible, not notifying
(20:49:21) [0x8adc408] [LocalCoverArtSearch.search] /usr/lib/rhythmbox/plugins/artdisplay/LocalCoverArtSearch.py:145: searching for local art for (full path to mp3 file here)
(20:49:21) [0x8adc408] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1293: new entry: (full path to mp3 file here)
(20:49:21) [0x8adc408] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1301: didn't get playing time; assuming 0
(20:49:21) [0x8adc408] [rb_audioscrobbler_is_queueable] rb-audioscrobbler.c:519: entry (full path to mp3 file here) is queueable
(20:49:21) [0x8adc408] [rb_shell_player_sync_with_source] rb-shell-player.c:2936: playing source: 0x8cf8e00, active entry: 0xb55ba2e0
(20:49:21) [0x8adc408] [show_controls] rb-visualizer-plugin.c:846: showing controls
(20:49:21) [0x8adc408] [rb_header_sync] rb-header.c:452: syncing with entry = (full path to mp3 file here)
(20:49:21) [0x8adc408] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0x8cf8e00
(20:49:21) [0x8adc408] [show_controls] rb-visualizer-plugin.c:846: showing controls
(20:49:21) [0x8adc408] [rb_shell_player_error] rb-shell-player.c:3421: playback error while playing: Failed to connect: Connection refused
(20:49:21) [0x8adc408] [error_cb] rb-shell-player.c:3574: exiting error hander
(20:49:21) [0x8adc408] [error_cb] rb-shell-player.c:3571: got error for unexpected entry (nil) (expected 0xb55ba2e0)
(20:49:21) [0x8adc408] [error_cb] rb-shell-player.c:3571: got error for unexpected entry (nil) (expected 0xb55ba2e0)
(20:49:21) [0x8adc408] [error_cb] rb-shell-player.c:3571: got error for unexpected entry (nil) (expected 0xb55ba2e0)
(20:49:21) [0x8adc408] [rb_shell_player_handle_eos] rb-shell-player.c:935: handling eos for (full path to mp3 file here)
(20:49:21) [0x8adc408] [rb_shuffle_play_order_get_next] rb-play-order-shuffle.c:198: choosing next entry in shuffle

```

Then after this, the log goes on to say it's trying the next file in the list. What ends up happening when I click play is that the song name will come up, then a split second later it will go onto the next song, and this will continue for about 10 songs or so, after which Rhythmbox just gives up and freezes.

I tried Banshee, but it too won't play.
I get the following error at the console when I try to play with Banshee:

> 
[Error 21:09:43.680] GStreamer resource error: Failed
[Error 21:09:44.345] GStreamer resource error: Failed
[Error 21:09:45.037] GStreamer resource error: Failed


Since Rhythmbox also uses GStreamer I suspect it's a problem with the library.

Any thoughts on this?

---

### Post by Volt9000 on 2009-05-24
*bump*
Anyone know about GStreamer?

---

