---
title: "maverick + lirc + antec veris usb IR"
date: 2010-10-24
forum: Multimedia Software
---

### Post by charlesalle on 2010-10-24
Hi !

I have bought a Antec Veris USB IR receiver (Soundgraph 15c2:0042) and a Sejin IR Keyboard.

First of all, I have tried to make lirc work with the IR receiver. Either with aptitude version of lirc or the compiled 0.8.7, I am not able to make it work.

When I am trying to use it with irrecord, (irrecord -d /dev/lircd recfile), it gets no signal from the included remote (Antec Veris RM100).

Has anyone got it to work ? Can anyone please give me some instructions ?

Second; I would like to know if this imon receiver could work with my Sejin IR Keyboard ?

Many thanks !!!

---

### Post by charlesalle on 2010-10-24
I forgot to say that I read the other threads and when I am trying to purge and reinstall lirc, this is what I get : 

(selecting the "Linux input layer (/dev/input/eventX)")

```
sudo aptitude install lirc
The following NEW packages will be installed:
  lirc 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/626kB of archives. After unpacking 2,707kB will be used.
Preconfiguring packages ...              
Selecting previously deselected package lirc.
(Reading database ... 160027 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.8.7~pre3-0ubuntu1_i386.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up lirc (0.8.7~pre3-0ubuntu1) ...
 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...fail!

```

---

### Post by charlesalle on 2010-10-24
I solved the first part; when reinstalling lirc and doing a dpkg-reconfigure lirc, the hardware.conf file had no reference to the device.

Does anyone knw about the Sejin keyboard ?

I mean, some things are unclear for me ; protocol and compatibility between receivers and remotes.

Thanks !

---

