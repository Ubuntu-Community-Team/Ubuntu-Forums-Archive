---
title: "Latest VLC doesn't full screen properly"
date: 2009-07-29
forum: Multimedia Software
---

### Post by xenogia on 2009-07-29
After getting the latest VLC update today, videos dont fullscreen properly.  This is what it does.

[IMG]http://cca.xenogiagames.com/uploads/9a65075366017a9e133b3ce96765fd17.png[/IMG]

I've tried both X11 and OpenGL and it does the same thing, any ideas how to resolve this issue?

---

### Post by rannable on 2009-07-29
It could just be an incompatibility with your vid card, are you using 32bit ubuntu and 32bit vlc? also did you get VLC from the repo or from the website? I would be tempted to use 64 bit ubuntu as i find it to be way more reliable...

---

### Post by vinutux on 2009-07-29
Install from this repo [https://launchpad.net/~c-korn/+archive/vlc]("https://launchpad.net/~c-korn/+archive/vlc")

---

### Post by xenogia on 2009-07-29
> **rannable said:**
> It could just be an incompatibility with your vid card, are you using 32bit ubuntu and 32bit vlc? also did you get VLC from the repo or from the website? I would be tempted to use 64 bit ubuntu as i find it to be way more reliable...


I figured out what the problem is, seems when Ubuntu did the kernel update to 2.6.28-14 VLC went a bit haywire.  What I did was just set all the preferences to default in VLC and its working fine.  Oh and I am using 64bit, but everything is working fine now.  Thanks for your help though :)

---

