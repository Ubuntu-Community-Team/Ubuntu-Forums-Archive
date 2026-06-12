---
title: "dual monitors, mouse stuck on one screen"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by c4mden on 2006-08-24
hello all!

i'm fairly new to the whole ubuntu game, but i recently got a second monitor and a second video card set up, and battled with xorg.conf, and finally i can see stuff on both monitors.  i'm not using twinview, or xinerama, or anything fancy.  i just want two monitors, with two desktops.

that all works great.  however, i can't move my mouse to the second monitor!  it shows up nice, with a pretty desktop and icons and all, i just can't access it!

i'm guessing it's something simple.  if anyone could point me in the right direction, that'd be great.  and if anyone needs it, i'd be happy to post my xorg.conf.

---

### Post by pap3rtiger on 2006-08-25
yea im having the same problem, some people have sugesting installing automatix, and then configuring twinview from nvidia. and youll need to edit the config file with the dual monitor resoultions youll want to run. i got it working once, but it was a two day afair.good luck

---

### Post by c4mden on 2006-08-25
well, twinview wouldn't work for me, since i'm using two ati cards.

i finally got it though!  it ended up that i had a typo in the ServerLayout section, and had referred to my second screen by the wrong name.  the screen still showed up fine, but since the serverlayout section couldn't find it, the mouse wouldn't recognize it.

stupid x never gave me a decent error message, but i found this nice program on the boards here called xorg-edit that gave me a good debug notice when i tried to open my xorg.conf file in it!

---

### Post by nicminus on 2008-03-25
> **c4mden said:**
> i finally got it though!  it ended up that i had a typo in the ServerLayout section, and had referred to my second screen by the wrong name.  the screen still showed up fine, but since the serverlayout section couldn't find it, the mouse wouldn't recognize it.

Haha, thanks a lot for this - in my case, it was the RightOf "Screen1" that I had misspelled!

---

