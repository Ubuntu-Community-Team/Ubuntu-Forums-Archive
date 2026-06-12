---
title: "Plymouth: Messed up graphics?"
date: 2010-12-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-12-05
Logo and dots seem a bit distorted on two of my machines (Nvidia BLOB + framebuffer, Nouveau):

[img]http://img.xrmb2.net/images/221310.png[/img]

Do you see this too?

---

### Post by nperry on 2010-12-05
+1 on this one. Has been around for a couple of days.

---

### Post by dext on 2010-12-05
what Version of Plymouth does Natty use? 0.8.2? maybe it should get the latest 0.8.4 which would probably fix that dodgy Distortion

---

### Post by plun on 2010-12-05
This is the last update....

[https://lists.ubuntu.com/archives/natty-changes/2010-December/thread.html](https://lists.ubuntu.com/archives/natty-changes/2010-December/thread.html)

> plymouth (0.8.2-2ubuntu7) natty; urgency=low

  [ Steve Langasek ]
  * Refactor ubuntu-text theme to allow setting colors and text via settings
    in the plymouth theme file, and have plymouth-theme-kubuntu-text depend
    on ubuntu-text instead of duplicating the code.
  * Bump the version strings from 10.10 to 11.04.  LP: #683994.

  [ Michael Terry ]
  * debian/plymouth.plymouth-stop.upstart,
    debian/plymouth.upstart:
    - Recognize uxlaunch as a display manager. (LP: #609163)


It has look like "****" for a long time for me....  but running on a SSD-disk so it only takes a few seconds;)

---

### Post by MacUntu on 2010-12-05
See [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/685352](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/685352)

---

### Post by Quackers on 2010-12-05
Same here for the last few days. 
Even with 1920x1200 Plymouth screen it a bit looks dodgy :-)

---

### Post by dino99 on 2010-12-05
> **MacUntu said:**
> See [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/685352](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/685352)

+1 on my end too

---

### Post by scradock on 2010-12-05
> **MacUntu said:**
> Logo and dots seem a bit distorted on two of my machines (Nvidia BLOB + framebuffer, Nouveau):

[img]http://img.xrmb2.net/images/221310.png[/img]

Do you see this too?
Yes, identical appearance with elderly ATI graphics (200M Radeon Xpress). Not something special to nvidia this time.....

---

### Post by go7Ul1ai on 2010-12-05
I also get the same, on an intel graphics chipset.

---

### Post by rajeev1204 on 2010-12-11
Same here. AMD Radeon 4850 with proprietary drivers or open source ones.

---

### Post by screaminj3sus on 2010-12-11
Same here hd2600 oss drivers.

---

### Post by Starks on 2011-01-01
still present, plus other themes don't work.

---

### Post by Harry33 on 2011-01-01
> **Starks said:**
> still present, plus other themes don't work.

I use the Plymouth-theme-solar.
But as everyone else is experiencing, the antialiasing does not work.

---

### Post by ronacc on 2011-01-01
you mean it's supposed to look different ? it has always looked like that on my nvidia box .

---

### Post by Harry33 on 2011-01-01
> **ronacc said:**
> you mean it's supposed to look different ? it has always looked like that on my nvidia box .

If you ask me, yes it should look different, more polished.
Now the borders of the text and the graphics are rough.

See the bug #685352
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/685352](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/685352)

---

### Post by hugmenot on 2011-01-03
Looks like a color palette issue, i.e., no RGB is available (16-bit, 24-bit, 32-bit)

---

### Post by cariboo on 2011-01-03
It wouldn't surprise me that the design team is having a bit of fun at our expense, just like the interim wallpaper during the Maverick release . :)

---

### Post by Harry33 on 2011-01-04
> **cariboo907 said:**
> It wouldn't surprise me that the design team is having a bit of fun at our expense, just like the interim wallpaper during the Maverick release . :)

Now that was fun alright. :p

---

