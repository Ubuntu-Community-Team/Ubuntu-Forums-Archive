---
title: "cannot play media files over network"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by GTCG on 2007-01-09
Hello,

I am really new to linux and i have encountered a problem when I try to play media files. I have Totem player installed, and Mplayer media player. I have a fileserver here at my home, running on linux(gentoo ) as well. There are a bunch of media files and other stuff on it, but when I try to play media files that are on that fileserver from my computer(laptop) it simply does not work.

The totem player says he cannot read from the "resource" and when I try to play the file with Mplayer it simply sits there and does nothing, no error message, just plain nothing. I have mounted all my network drivers via samba, so I can access them from here. When I try to play files locally, it works.

How do I access my network media files with totem or Mplayer and play them?

Thanks in advance!

---

### Post by meng on 2007-01-09
VLC should be network-aware, at least many folks say so, and it is in my own experience.

Totem and Mplayer can play files IF you mount the samba share, e.g.:
sudo mount -t smbfs -o username=****,password=**** //192.168.0.5/sharename /mnt/point

---

### Post by gosh on 2007-01-09
I had the same problem with Ubuntu.
I created a static mount point and used fusesmb to make a connection to my share network sources.

See this for a guide: [http://www.ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb](http://www.ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb)
Works for gnome as well.

---

