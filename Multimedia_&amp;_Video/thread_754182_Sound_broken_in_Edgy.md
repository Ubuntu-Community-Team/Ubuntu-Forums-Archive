---
title: "Sound broken in Edgy"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by 1337hippo on 2008-04-13
Hi, for the last few days my sound has been really screwy. Most of the time, when I try to open a music file Totem opens up and hangs. I've also tried Amarok and VLC and they also stop responding. Youtube sometimes works and sometimes makes firefox die.

```
richard@gR0iD:~$ sudo lshw -C sound
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
```

when I go to System>Preperences>Sound and hit the "Tests", the window freezes.

Thanks for your time

edit- sorta unrelated, but I am using 5.1 surround speakers and I can only get the subwoofer and left and right to work. The other 3 don't work.

---

### Post by 1337hippo on 2008-04-13
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```
+ restart seems to have fixed the sound problem. Strange, because I am running on a 2 day old install of Ubuntu.

If anyone could help me with the surround sound that would be great

---

