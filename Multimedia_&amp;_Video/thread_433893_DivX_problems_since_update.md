---
title: "DivX problems since update"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by Steve- on 2007-05-05
I had all media types running perfectly in 6.10, but after updating, video files no longer play properly in Kaffeine, gxine or xine.
They do in Totem, but with somewhat less quality than I get with Kaffeine on my 6.10 desktop.

I've attached a screenshow of what I'm seeing, any ideas on how I can fix this?

Steve

---

### Post by disturbed1 on 2007-05-06
It's your driver setting. Change the output driver that Xine uses, try XV.

---

### Post by Steve- on 2007-05-06
xv doesn't work.
xshm works, but isn't great quality (you can see lines across it), definitely not as good as my desktop or what it used to be before the update.
sdl works but will not resize to fullscreen.


Why did anything change during the update anyway? Is it possible to get rid of everything and start again with the default values (which worked very well, and still do on my 6.10 desktop)

---

### Post by disturbed1 on 2007-05-06
You could try [COLOR=Red]sudo dpkg-reconfigure xserver-xorg [/COLOR]as a last resort.

What type of graphics card do you have? XV should work, on most cards. Even with Beryl installed and an Nvidia FX5500 XV overlay works with VLC, Mplayer, and Totem. Do you have the binary driver installed (if needed) and overlay enabled?

---

