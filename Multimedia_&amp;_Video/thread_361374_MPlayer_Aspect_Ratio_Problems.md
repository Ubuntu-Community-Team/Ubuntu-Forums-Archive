---
title: "MPlayer Aspect Ratio Problems"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by nonfiction330 on 2007-02-14
Hi

I have found a few problem with MPlayer when I am playing videos with it.  I am using a wide screen labtop so it seems that the aspect ration of the movie is wrong when it is played.  All of them are stretched horizontally.  I can fix the aspect if I switch -vo to x11 but I can't go full screen with it.   Anyone have any idea how to fix this problem?

Thanks

---

### Post by Vincent_Lin on 2007-02-14
Hi,

Do man mplayer and check out -monitoraspect option.   It tells mplayer what aspect ratio your monitor has and adjust the dimentions of video clips you are playing accordingly.  It can be combined with -fs option.

Vincent

---

### Post by ogrigorov on 2007-02-14
I know what you're talking about.

edit ~/.mplayer/config, add the following:
monitoraspect=1680/1050

or whatever your resolution is.  Restart Mplayer.  That should fix it, I guarantee!   :)  cheers!

---

### Post by reinfallt on 2008-02-11
I have an lcd tv with 1360x768 resolution as a secondary screen. Can I configure it separately or do I have to change the config-file depending on which screen i'm watching?

---

