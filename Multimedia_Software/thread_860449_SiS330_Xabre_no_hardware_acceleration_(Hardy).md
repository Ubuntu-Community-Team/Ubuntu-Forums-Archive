---
title: "SiS330 Xabre no hardware acceleration (Hardy)"
date: 2008-07-15
forum: Multimedia Software
---

### Post by zoubidoo on 2008-07-15
Has anyone succeeded in getting hardware acceleration to work for this card?  

```
$ lspci | grep -i display
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter (rev 01)

```
The drivers seem to be available:
```

$ slocate sis_drv
/usr/lib/xorg/modules/drivers/sis_drv.so.orig
/usr/lib/xorg/modules/drivers/sis_drv.so

```

xorg.conf is the default generated during installation.

glxinfo shows: 
```
$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

```
Then segfaults.

Is this misconfiguration or a bug?
Cheers,
Z.

PS Xorg log file attached.

---

### Post by zoubidoo on 2008-07-15
Attempting to attach log file again. (Needed to be bzipped because of size limits).

---

### Post by zoubidoo on 2008-07-16
I looked into this a bit further and found the following bad news.

From [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/44627](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/44627)
> 
From [http://www.winischhofer.at/linuxsispart3.shtml#faq:](http://www.winischhofer.at/linuxsispart3.shtml#faq:)
Q: Tuxracer is terribly slow on my SiS 315/550/650/651/330/661/741/760/761/340/XGI Vx

A: DRI and hardware accelerated OpenGL/3D is not supported on these chipsets. I don't know how many times I must say this. And besides, I don't do any DRI related development.


and
> 
This is something that won't be worked on by Ubuntu developers, only upstream in the DRI project:
[http://dri.freedesktop.org/wiki/SiS](http://dri.freedesktop.org/wiki/SiS)


From [http://dri.freedesktop.org/wiki/SiS](http://dri.freedesktop.org/wiki/SiS)
> A DRI driver for the SiS300 series cards (300/305, 540, 630/730) is currently available in DRI CVS. A DRI driver for the SiS6326 and 530 cards is in development. The newer 315 and Xabre series chips are not supported; neither are the SiS-based Volari chips from XGI (Volari V3XT, V5, and V8).


That's bad news for 315 and Xabre owners.

SiS has a linux FAQ [here]("http://www.sis.com/support/support_faqs_16.htm"), but there is no mention of these models.

According to the [following post dating from 2002]("http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg04894.html"), SiS have not been helpful:
> 
> Has anybody talked to SiS about this beastie (Xabre) yet?  It's brand
> new and I can't even find a card for sale, but there are a few reviews
> floating about the net.  Might be nice to get a decent card supported in
> DRI before it hits EOL ;)

After having attempted to get something going with them through my employer 
trying to support both the 300 and the 315 (Their then current card that is 
now out on store shelves...), I'd say that it's an uphill battle.  We have an 
NDA with them, but they won't disclose anything other than the 2D and MPEG 
support portions of the chip to us.


**Note to self: Steer clear of SiS/XGI graphics cards.**

---

