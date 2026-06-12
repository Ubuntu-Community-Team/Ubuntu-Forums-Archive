---
title: "Possible bug - headphones volume is very loud when comparing to speakers"
date: 2018-09-01
forum: Multimedia Software
---

### Post by postcd on 2018-09-01
Hello,

i have problem like other member who have same computer (Dell D600) as me: [https://ubuntuforums.org/showthread.php?t=1554368](https://ubuntuforums.org/showthread.php?t=1554368)

The speakers volume is good, but when i connect headphones, the volume in it it extremely loud, have to have minimum volume possible and raising just one bit make it significantly louder.

Here is AlsaMixer debug script output:
[https://defuse.ca/b/6Qbhj4CI6GpfbXPuSIhghO](https://defuse.ca/b/6Qbhj4CI6GpfbXPuSIhghO) (p@ss: ubuntu)

---
In the meantime i manually decreased volume according to tutorial posted at [https://askubuntu.com/a/69206/456366](https://askubuntu.com/a/69206/456366)

sudo nano /etc/pulse/default.pa

Change the line that says  load-module module-udev-detect   into

  load-module module-udev-detect ignore_dB=1   

  Restart pulseaudio by typing the following in a terminal:

  pulseaudio -k   

Now open alsamixer:

  alsamixer 

decrease headphones volume

but classic volume changer on system bar does not change headphones volume anymore

But after applying [second best answer]("https://askubuntu.com/a/895794/456366") in above linked page, and a bit adjusting master/headphones/PCM volume in above launched alsamixer, then all seems to be working good, and no longer issue, though i think there is some bug that may be fixed so other people and me do not need to hurt their ears and go thru this process.

---

