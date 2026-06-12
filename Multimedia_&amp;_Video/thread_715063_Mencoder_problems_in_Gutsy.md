---
title: "Mencoder problems in Gutsy"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by whoopn on 2008-03-04
Alright here is the issue:

Whenever I try to play a DVD in Mplayer or Transcode using Mencoder I get the same error

```

gnome_screensaver_control()
(gmencoder:9725): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gmencoder:9725): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gmencoder:9725): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gmencoder:9725): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
*** Zero check failed in ifo_read.c:436
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
gnome_screensaver_control()The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
No bind found for key 'MOUSE_BTN2'.
gnome_screensaver_control()mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
*** Zero check failed in ifo_read.c:436
    for vmgi_mat->zero_3 = 0x00000000010000000000000000000000000000
gnome_screensaver_control()The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
No bind found for key 'MOUSE_BTN2'.
gnome_screensaver_control()Pasadas: [3]
Segmentation fault (core dumped)

```

What am I doing wrong?  What do I do to fix this?

---

