---
title: "ncmpcpp deletes song from playlist after playing, no volume"
date: 2013-05-12
forum: Multimedia Software
---

### Post by oldpilsbury on 2013-05-12
Pulled this configuration from the 'net, and I changed a few things with  colors and settings. At the end of a song, the songs deletes from the  playlist. Under volume it says n/a. Could someone offer a solution, or a  better script?

~/.ncmpcpp/config:

 ncmpcpp_directory = "~/.ncmpcpp"
 mpd music_dir = "~/Music/"
 mpd_connection_timeout = "5"
 mpd_crossfade_time = "3"
 playlist_disable_highlight_delay = "5"
 playlist_display_mode = "columns"
 browser_display_mode = "columns"
 incremental_seeking = "yes"
 autocenter_mode = "yes"
 header_visibility = "yes"
 statusbar_visibility = "yes"
 fancy_scrolling = "no"
 follow_now_playing_lyrics = "yes"
 display_screens_numbers_on_start = "yes"
 ignore_leading_the = "yes"
 lyrics_database = "1"
 song_columns_list_format = "(10)[blue]{l} (30)[green]{a} (30)[magenta]{b} (50)[red]{t}"
 colors_enabled = "yes"
 main_window_color = "white"
 header_window_color = "cyan"
 volume_color = "red"
 progressbar_color = "cyan"
 statusbar_color = "white"
 color1 = "cyan"
 color2 = "cyan"
 active_column_color = "cyan"
 active_window_border = "blue"

---

### Post by oldpilsbury on 2013-05-15
I figured out the song deletion issue. "R" toggles "consume" mode in ncmpcpp.

---

