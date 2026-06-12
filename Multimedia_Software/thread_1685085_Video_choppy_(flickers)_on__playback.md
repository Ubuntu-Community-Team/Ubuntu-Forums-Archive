---
title: "Video choppy (flickers) on  playback"
date: 2011-02-10
forum: Multimedia Software
---

### Post by SknHeD23 on 2011-02-10
Hi, I just upgraded to Ubuntu Maverick v 10.10 and loving it.  However, I have encountered a problem with playing any type of video whether it be Xvid, AVI, h264, MKV or AAC.  I have tried many players from smplayer, mplayer, kmplayer, vlc, etc. but I am still having the problems.  I have read some posts on here and I've disabled compiz, tried the X11 tweak and updated my Nvidia drivers.  I don't know if I am missing some type of codec or restricted plugin because I have ample space and resources are readily available while playing the video.  I am stumped at the moment, and thanks in advance for any help.

---

### Post by P4man on 2011-02-10
Do you mean video tearing? Like this:

[IMG]http://tdistler.com/wp-content/uploads/2010/07/v_sync.jpg[/IMG]

If so, try this quick and dirty solution:

```
gksudo gedit /etc/X11/xorg.conf
```

If that opens a xorg config file, add this at the bottom:

```
Section "Extensions"
        Option "Composite" "disable"
EndSection
```

Save, reboot.

---

### Post by SknHeD23 on 2011-02-11
Sorry, I couldn't come up with a good word to call it.  That helped, but it is still doing it.  Thanks for the fast reply.  Do you know of anything else I can do?

---

