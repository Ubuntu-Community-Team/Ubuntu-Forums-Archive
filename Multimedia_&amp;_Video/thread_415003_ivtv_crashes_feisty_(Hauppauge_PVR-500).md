---
title: "ivtv crashes feisty (Hauppauge PVR-500)"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by bnuytten on 2007-04-20
Okay here's the story in short. Have Edgy running fine, ivtv drivers and mythtv etcetera all working fine. Installed Feisty in a dual boot configuration on that same machine. Did not have to install/compile ivtv drivers. Sounds great!

Installed mythtv right away but did not work. After some fiddling around discovered that when testing /dev/video0 the whole thing crashes. Downloaded the ivtv source (v0.10.1) and compiled/installed manually but the driver looks the same (lsmod gives the same size) and it crashes also.

I had over three attempts now but the result remains the same. As soon as I run the following command (as root) the machine reboots.
```
cat /etc/video0 > my.mpg
```

Some extra  information:
```
lspci | grep video
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

dpkg --list | grep ivtv
ii  ivtv-utils                                 0.10.1-0ubuntu1                        utilities for use with the ivtv kernel drive
ii  libvideo-ivtv-perl                         0.13-3                                 Perl extension for using V4l2 in the ivtv pe

lsmod | grep ivtv
ivtv                  134544  0 
i2c_algo_bit            8712  1 ivtv
cx2341x                12804  1 ivtv
tveeprom               15888  1 ivtv
videodev               28160  1 ivtv
v4l2_common            25216  5 cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15236  2 ivtv,videodev
i2c_core               22784  8 i2c_ec,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom,i2c_viapro
```

Read trough the source code REAME's, reverted to the "original" Feisty drivers but none of this seems to work. Guess the original drivers are the same as 0.10.1.

---

### Post by michaelboord on 2008-01-20
Yea I'm having the same problem... with a pvr-500 card


Ivtv is also partly integrated into the kernel so you can't just upgrade from the
ivtv source :( 

Even when I don't use the card or mythtv the pc crashed after a while or high load :( 

First thought it wasn't related to the PVR card..
But now I removed the card an no more problems. 


Was thinking maybe a defective card but I also borrowed my brothers PVR 150 
card and the same thing..

Even when it is just unused in a PCI slot it causes the computer to crash after a while. 

:(

---

