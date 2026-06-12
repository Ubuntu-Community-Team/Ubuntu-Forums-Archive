---
title: "s-video to TV only; works until login screen"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by rrands on 2007-01-13
I know similar problems have been mentioned, but I haven't seen any replies, and my problem seems different enough than others, so I added a new post.

I am trying to use a television as my only video output on a DELL DIMENSION 8200 BIOS revision A01. I am running edgy Edubuntu. I have had it running perfectly with great video on a normal CRT.

When I hooked it up to my TV from the s-video out, I get video on the TV through the DELL BIOS, I see that GRUB works. Then I see the orange edubuntu boot screen. the status bar completes and then the screen goes to an all black screen with a cursor up at the top left for a second and then it all goes blank. It doesn't go to the user login screen like normal.

The computer sounds like it is on and ok, but the video just goes out. It happens every time. 

Also, right before it goes to the black screen with the cursor, the screen does a little flash with some snow/fuzz for a split second. not something I saw normally with the monitor. 

Any help?

I don't know if it is a hardware or software problem, but I switched out the video card with a similar one (both nVIDIA g-force 2mx with TV out) and same result.

Thanks.
new ubuntu user. (I don't really know how to use linux, but I can follow directions pretty well)

---

### Post by pay on 2007-01-13
I think that you need to use the proprietary video driver for that.

---

### Post by rrands on 2007-01-14
can you explain further? I'm assuming you mean I need the proprietary driver for the nVIDIA card. How/where do I get it, and how do I know what driver I need? How do I put it on the computer if I can't get in past the login. Sorry if these questions seem obvious. I've really only used windows and mac osx up to this point.

thanks
rrands

---

### Post by pay on 2007-01-14
Boot into the recovery mode and type ```
sudo apt-get install nvidia-glx nvidia-kernel-common
```Provided you have the universe repository opened in /etc/apt/sources.list. If you don't just add universe at the end of every line. And then switch to the new driver ```
sudo nano /etc/X11/xorg.conf
```replacing "nv" with "nvidia" in Section "device"

---

### Post by blackmh on 2007-01-14
You should search forums a bit before trying to enable tv-out. It can save you a lot of trouble.

---

