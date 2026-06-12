---
title: "Video playback with AIGLX (see video inside topic)"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by hispanico87 on 2007-12-01
I've this problem with video playback:

[http://www.youtube.com/watch?v=V6RX9hLF-8k](http://www.youtube.com/watch?v=V6RX9hLF-8k)

I'm using 8.43 fglrx driver with AIGLX and compiz-fusion enabled! I had the same problem also with 8.42.3 driver.
I think the problem is connected to AIGLX becouse with XGL there isn't any problem.
I partially solved problem setting "change method for fullscreeen mode" in VLC. 
Sorry for my very bad english.
Thanks for any help.

---

### Post by Melcar on 2007-12-01
Make sure the video output mode is set to X11;  you can change it with the settings menu in VLC.  This is currently a limitation of ATI's driver (you can't use Xv nor opengl while Compiz+AIGLX is running).  All other video players must be using X11 to output video as well (Totem, Mplayer, etc.).

---

