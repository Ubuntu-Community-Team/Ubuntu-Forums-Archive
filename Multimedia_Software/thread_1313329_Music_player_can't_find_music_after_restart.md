---
title: "Music player can't find music after restart"
date: 2009-11-03
forum: Multimedia Software
---

### Post by odsus1 on 2009-11-03
I'm fairly new to Ubuntu and i love it.  The only problem is that whatever media player I try to use will not remember where my music is after a restart and I have to reload it again (with over 100 gb that takes a while). I am sure there is something simple that I haven't done can anyone help?  I have tried on Hardy and (currently) Jaunty using Amrock rhythmbox sogbirdand at least two more that I can't remember right now.

System: 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.66GHz
stepping    : 9
cpu MHz        : 2679.911
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no

MemTotal:        1018648 kB
MemFree:          119648 kB
Buffers:          150464 kB
Cached:           418012 kB
SwapCached:            0 kB
Active:           579756 kB
Inactive:         224436 kB
Active(anon):     292888 kB
Inactive(anon):        0 kB
Active(file):     286868 kB

---

### Post by IAmNoodle on 2009-11-03
Are you using just Ubuntu, or is it set up alongside another operating system that your music is on? With my computer, I have Ubuntu/Windows XP dual boot setup, with my music (and wallpaper) on the Windows partition, but the only way any music player can find any of it is if I click 'places' and click on system, which (forgive my lack of expertise if I'm wrong) mounts the partition as a removable drive, which then gives access to the pic for my wallpaper and my music.

I've yet to find a way, or ask, how to solve this problem

If Ubuntu's your only OS, then this would be useless to you, but probably made a nice short story for you :)

---

### Post by odsus1 on 2009-11-03
I have a clean install of jaunty with no other os's, however some (not all) of my music is on an nfts partition.

---

### Post by michy99 on 2009-11-03
If you set up the partition to mount at boot, it should solve your problem. There are several ways to do this. Here is one:

[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by odsus1 on 2009-11-06
I finaly had some time and set up the NTFS Config Tool and mounted the two ntfs drives and everything seems to work great now. Thanks alot michy99.

---

