---
title: "Mythbuntu 9.10 - can't use Terratec 2400i"
date: 2009-12-05
forum: Mythbuntu
---

### Post by lafaki on 2009-12-05
Hi,

I just installed Mythbuntu 9.10 (both backend and frontend on the same machine).

I have a Terratec 2400i dual DVB-T card which MythTVBackend can't find. I tried to follow the instruction in the below link (Experimental driver-recommended) 
[http://linuxtv.org/wiki/index.php/Media-Pointer_MP-S2%C2%B2](http://linuxtv.org/wiki/index.php/Media-Pointer_MP-S2%C2%B2)
and when I run the make command, I get the below errors:

make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/lafaki/mediapointer-dvb-s2/v4l/firedtv-1394.o
/home/lafaki/mediapointer-dvb-s2/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/lafaki/mediapointer-dvb-s2/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
.... 

For some reason it can't find the header files.

Any ideas how to overcome this problem?


Is there anyone that managed to make the Terratec 2400i work in Mythbuntu 9.10?


Many Thanks!
Akis

---

