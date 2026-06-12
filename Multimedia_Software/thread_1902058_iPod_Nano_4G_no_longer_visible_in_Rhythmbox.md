---
title: "iPod Nano 4G no longer visible in Rhythmbox"
date: 2011-12-29
forum: Multimedia Software
---

### Post by andrewkirk on 2011-12-29
Hello. I have an iPod Nano that until today I synced with my Ubuntu PC via Rhythmbox. I recently acquired an iPod Touch (software version 4.2.1) and spent a few hours trying to get the Ubuntu PC to see that, without success. Following the instructions in various forum threads, I installed libimobiledevice1 and libimobiledevice1-dbg and fiddled around generally with packages in that area. Currently libimobiledevice1-dbg is not installed because I tried uninstalling it at one stage, then it wouldn't let me reinstall it, saying:

"E: /var/cache/apt/archives/libimobiledevice1-dbg_1.0.6-1ubuntu1~lucid3_i386.deb: trying to overwrite '/usr/lib/debug/usr/lib/pyshared/python2.6/imobiledevice/_imobiledevice.so', which is also in package libimobiledevice0-dbg 0"

Meeting with no success for my ipod touch using any of the suggested methods, I gave up and went back to my Nano, only to find to my horror that Rhythmbox could no longer see it. Doubtless this is a consequence of the other changes I made trying to get the touch visible.

What happens when I connect the nano now is that it automatically mounts as storage and opens a Nautilus window showing the contents. But neither Rhythmbox nor Banshee can see it.

I would be very grateful for any advice anybody can offer about how to get my Ubuntu talking to the nano again.

My system is Ubuntu 10.04 LTS 32 bit, using Rhythmbox 0.12.8.
The Nano is 4th gen 8GB.

Thank you

---

### Post by andrewkirk on 2012-01-12
Well what do you know?! I used Synaptic to remove Rhythmbox and then reinstalled it, and it could see the Nano again.:o:)

---

