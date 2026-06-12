---
title: "Exaile in Gusty"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by monsieurdozier on 2007-11-01
I removed my old Feisty partition and replaced it with a Gusty partition.  I've worked out most of the kinks, but I'm still having a problem with Exaile.

I reinstalled exaile and added the shoutcast plugin.  However, when it tries to import the playlist, exaile crashes.

Is anyone else having this problem, and what can I do to fix it?

---

### Post by santiagoward2000 on 2007-11-01
HI!
I'm using Exaile in Xubuntu Gusty and had no problems with it. I don't use any plugins with it. Have you tried to disable the shoutcast plugin and see what happens?

---

### Post by Neon Lights on 2007-11-01
type exaile in the terminal and post the output. ^^

---

### Post by monsieurdozier on 2007-11-01
Exaile itself is running fine, no problem with any of my song files.  I'm just having problems with the radio streams.

[Quote=Terminal Output]
Plugins 'Shoutcast Radio' version '0.2' loaded successfully
Created db for thread Thread-2
{'Thread-2': <sqlite3.Connection object at 0x89ba2f0>}
Closed db for thread Thread-2
Using multimedia keys from: gnome
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/****/.exaile/saved/playlist0000.m3u
/usr/share/exaile/xl/trackslist.py:125: GtkWarning: gdk_pixbuf_copy_area: assertion `src_x >= 0 && src_x + width <= src_pixbuf->width' failed
  star.copy_area(0, 0, star_size, star_size, full_image, star_size * x, 0)
Last playlist loaded
Loading page 0
Importing [http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=106789&file=filename.pls](http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=106789&file=filename.pls)
Warning: Gstreamer equalizer element not found, please install the latest gst-plugins-bad package
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3
Killed
[/Quote]

If I'm reading this correctly, I should get the Gstreamer equalizer.

I downloaded the Gstreamer extra plugins from Add/Remove Programs and it works, no problem.

Thanks much.

-Monsieur Dozier

---

### Post by Neon Lights on 2007-11-01
Glad I could help. ^^ When ya got a problem, always look at the terminal output. xD

---

