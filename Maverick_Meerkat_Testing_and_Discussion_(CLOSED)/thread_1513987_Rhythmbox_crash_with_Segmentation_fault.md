---
title: "Rhythmbox crash with Segmentation fault"
date: 2010-06-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by darkhole on 2010-06-20
Rhythmbox is crashed when I tried to play any song. The only weird thing is that Ubuntu one deamon is disable by myself.

This is the output of the crash of rhythmbox -d:

(09:08:28) [0x1b87f60] [window_focus_cb] rb-mmkeys-plugin.c:153: window got focus, re-grabbing media keys
(09:08:29) [0x1b87f60] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:807: entryview changed
(09:08:29) [0x1b87f60] [rb_shell_clipboard_sync] rb-shell-clipboard.c:600: syncing clipboard
(09:08:29) [0x1b87f60] [rb_entry_view_row_activated_cb] rb-entry-view.c:2160: row activated
(09:08:29) [0x1b87f60] [rb_entry_view_row_activated_cb] rb-entry-view.c:2164: emitting entry activated
(09:08:29) [0x1b87f60] [rb_shell_player_entry_activated_cb] rb-shell-player.c:2689: got entry 0x38be580 activated
(09:08:29) [0x1b87f60] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3106: setting playing source to 0x1d88220
(09:08:29) [0x1b87f60] [rb_shell_player_sync_with_source] rb-shell-player.c:2930: playing source: 0x1d88220, active entry: (nil)
(09:08:29) [0x1b87f60] [rb_shell_set_window_title] rb-shell.c:2168: clearing title
(09:08:29) [0x1b87f60] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3365: Did not get playing entry : return -1 as length
(09:08:29) [0x1b87f60] [rb_shell_player_sync_buttons] rb-shell-player.c:3025: syncing with source 0x1d88220
(09:08:29) [0x1b87f60] [rb_shell_playing_source_changed_cb] rb-shell.c:2045: playing source changed
(09:08:29) [0x1b87f60] [construct_pipeline] rb-player-gst.c:686: using gconfaudiosink
(09:08:29) [0x1b87f60] [construct_pipeline] rb-player-gst.c:692: setting profile property on audio sink
(09:08:29) [0x1b87f60] [pipeline_op] rb-player-gst-helper.c:341: not using pad blocking, calling op directly
(09:08:29) [0x1b87f60] [really_add_filter] rb-player-gst-helper.c:400: adding filter 0x3404170
Fallo de segmentación
darkhole@maquis:~$


Fallo de segmentación = Segmentation Fault

---

### Post by eb sol on 2010-09-06
I had the same problem ...

First save your playlists ..

you can find it in ~/.local/share/rhythmbox/playlists.xml , then :

```
find ~ | fgrep rhythm
```

delete all old rhythmbox folders :) ..

finally reinstall it .. and put back you playlists ;)

it worked for me  :o ..

---

