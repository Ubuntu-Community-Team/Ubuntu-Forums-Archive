---
title: "Sound&amp;Video in Ubuntu 8.04 vs 7.10"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Peder_Erickson on 2008-06-10
I'm wondering what changed between the versions.  In Ubuntu 7.10 I have Dual Screens (NVidia video card) and I can have Banshee music player, and a game running at the same time, as well as many other applications, and hear the sounds from all of them

In 8.04, I cannot activate the second monitor via the Nvidia configuration utility, (I end up with my main screen running at 800X600, instead of 1440X900, and the other screen just stays off) and I only have sound coming out of one program at a time.

Can anyone tell me how to get these two things working properly in 8.04?

I'd love to hear my music while playing a game again.:(

edit - I've gone through some tutorials on getting sound to come out of multiple applications at the same time, but none of them seem to work:confused:

---

### Post by Peder_Erickson on 2008-06-11
bump

can anyone help?

---

### Post by Peder_Erickson on 2008-06-11
Bump

anyone?

---

### Post by wolfen69 on 2008-06-11
do for video:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
for sound, do [THIS]("http://ubuntuforums.org/showthread.php?t=776739")

---

### Post by Peder_Erickson on 2008-06-11
I did all of the steps, and now no games will work...

:confused:

Why doesn't the sound work right after the install, like 7.10 did?

I'm guessing that the reconfigure of xorg was to reset the monitor, but I want to have dual screens, like I have in 7.10 and windows.

---

### Post by crjackson on 2008-06-11
I can't really help you with the dual monitors myself as I've never used them.  As for the sound, the problem is the new Pulse Audio layer.  It's not really prime-time yet and many people were upset that it was included since it's not done cooking just yet.  It will grow and get better but it's not there yet.

If you're not happy with 8.04 and want 7.10 performance, just go back to 7.10 until 8.04 gets the bugs worked out that are of particular concern.  I use both versions and 7.10 is a great version.  Half of my systems still use 7.10 as there was no reason to upgrade them.

8.04 works great on my other systems and fixed a few problems I was having under 7.10.

Just choose what works best for you and forget about the version numbers.

Latest is not always Greatest for everyone...

---

### Post by Peder_Erickson on 2008-06-11
Yeah, I can see that, the main reason was WINE, I wanted to try the newer version, an app that I wanted to use just crashed out on 7.10,  I installed 8.04 on the main HD, and installing it there made Windows XP work again

I still have 7.10 running, but I have a large FAT partition on that disk, and fsck slows the booting process down because it scans that partition EVERY time it boots.  Other than that 7.10 is working perfectly

I got games working again, it lost the nvidia driver in xorg.conf, I just used 

```
sudo nvidia-xconfig
```

After that, all OpenGL games started working again.  I think I will keep 8.04, but 7.10 will be the default.

---

### Post by Gina on 2008-06-12
I think I'll have to go back to 7.10 for audio stuff - 8.04 with PulseAudio just won't seem to work with Audacity and some other stuff.  In most ways 8.04 is a great improvement but it seems PulseAudio was a mistake as it's just not ready.  I'm also running 8.10 Intrepid Ibex on my test machine so will be watching for improvements in this area.

---

