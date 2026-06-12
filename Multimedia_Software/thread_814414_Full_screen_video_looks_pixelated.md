---
title: "Full screen video looks pixelated"
date: 2008-05-31
forum: Multimedia Software
---

### Post by sparkguitar05 on 2008-05-31
I have a bunch of high-quality 720x480 videos on my hard drive. When I would watch these in fullscreen in Windows XP or Ubuntu 7.10, they looked perfectly fine. Ever since I upgraded to Ubuntu 8.04 these same videos look extremely pixelated and nearly unwatchable. It doesn't matter which program I use, it looks like crap no matter what.

---

### Post by pepito9 on 2008-05-31
Did you install your video drivers?

The same thing happened to me, until i realized i didn´t install the drivers.

---

### Post by sparkguitar05 on 2008-05-31
I'm using the ATI Restricted Driver.

---

### Post by Bakon Jarser on 2008-05-31
Were you using different codecs?  Maybe before you were using the w32codecs from the medibuntu repository.

---

### Post by sparkguitar05 on 2008-05-31
It's video captured from a mini-DV camera using software in Windows.

---

### Post by Bakon Jarser on 2008-05-31
So you're using this windows program in wine to watch the videos?  If you're using a linux media player then you are still using codecs.  What kind of videos are they?  WMV? AVI?

---

### Post by sparkguitar05 on 2008-05-31
I've tried watching them in Linux with VLC and Totem.  They are AVI files.

---

### Post by spandanj on 2008-07-08
any solution to this problem? with compiz ON?

i still get pixelated video on fullscreen.

fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

I have compiz ON.

---

### Post by spandanj on 2008-07-08
i reported a bug with launchpad. please write comments on there to put pressure on developers to solve this.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/231519](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/231519)

---

