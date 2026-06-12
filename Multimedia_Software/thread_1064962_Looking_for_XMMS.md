---
title: "Looking for XMMS"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Silvernail on 2009-02-09
I listen to a lot  of internet radio. I would like an app that I can put into the top tray and hard code the address into it.

On  another distro I used XMMS. When I try to apt-get it I get this message.> 
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

Where can I get it. Or equivalent. The thing I liked about XMMS is you could hover the curser over the icon and see who was playing.

Thanks
Dave

---

### Post by cariboo on 2009-02-09
HAve a look [here]("http:///www.pvv.ntnu.no/~knuta/xmms/") for xmms debs.

Jim

---

### Post by Coreigh on 2009-02-09
XMMS seems to have become XMMS2 in 8.10 (Intrepid)
[http://packages.ubuntu.com/intrepid/sound/xmms2](http://packages.ubuntu.com/intrepid/sound/xmms2)

Audacious is similar simple and easy to use too.
[http://packages.ubuntu.com/intrepid/sound/audacious](http://packages.ubuntu.com/intrepid/sound/audacious)

---

### Post by Silvernail on 2009-02-09
Cariboo and Coreigh

I install both and no joy. the image is so small I can not see them with these old eyes plus dark blue on black fonts don't help either.

I did manage to find where to enter a URL on both but have not gotten it to stick.

This is just to bring you up to date. I'm not through yet.

---

### Post by joron on 2009-02-15
Silvernail,

You should be able to use double size in xmms. Ctrl+D or preferences to change the size

---

### Post by markbuntu on 2009-02-15
If you miss your xmms (not xmms2) and would like to have it back:
i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

---

