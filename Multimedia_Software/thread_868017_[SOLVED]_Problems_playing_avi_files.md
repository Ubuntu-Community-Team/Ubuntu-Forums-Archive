---
title: "[SOLVED] Problems playing avi files"
date: 2008-07-23
forum: Multimedia Software
---

### Post by heiowge on 2008-07-23
Been having problems playing some avi files that I'm sure are fine.
This problem is only recent, but I can't trace it...

Playing with windows media player under XP - fine
Playing with vlc - thick green bar at the top of the video
Playing with totem - thin vertical green bar just to the right of the middle of the display, then video is severely skewed diagonally like this /

Other files play fine - it's just a few that do that.

Any ideas?

---

### Post by heiowge on 2008-07-24
bump

---

### Post by XxsydenxX on 2008-07-24
Its actually not a problem with any of your linux players so much as a problem with the codecs for the players...some avi files are encoded a tad differently and windows has more support for that..ubuntu however is only working its way up to it...for instance im an anime fan and i downloaded a certain anime from via torrent...they were avi's that were encoded to the point vlc or ANYTHING could not read them correctly thus i had  no video and only sound. but when i played my other anime it played just fine.

---

### Post by rockstarrem on 2008-07-24
If GStreamer Video Plugin is already installed you can try uninstalling it and installing it again and seeing if it helps. You can do this by typing "avi" in the search box in Applications > Add/Remove.

---

### Post by heiowge on 2008-07-24
Ininstall / reinstall not fixed it.:(

---

### Post by faical117 on 2008-07-24
try with "Xine extra plugins" & mplayer :)

---

### Post by heiowge on 2008-07-25
I get an error message with Xine extra, saying that my PC isn't supported (i386).  It suggests that maybe the vendor decided not to support my PC.

---

### Post by mcduck on 2008-07-25
Could you check what codec was used to compress the video in your file? At least VLC should be able to tell you that..

AVI is not a video format, it's a container file, and can contain sound and video coded in almost any format. Because of this there's never any guarantee that an AVI file will play fine, without knowing the codecs used.

---

### Post by heiowge on 2008-07-25
Xvid for one and Divx MPEG-4 Version 5 for the other.

---

### Post by Archmage on 2008-07-25
Did you try mplayer?

---

### Post by heiowge on 2008-07-25
Just.  I get sound and no picture whatsoever!

---

### Post by indiana_crook on 2008-07-25
Here, check out this web site.  When I install ubuntu fresh I use this site to get the setup I want.  Everything works great.  Give it a try.

[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)

---

### Post by heiowge on 2008-07-25
So far, it seems to have fixed VLC but not totem!  bizarre!  Cheers.

---

