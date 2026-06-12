---
title: "Antec fusion and Hauppauge MCE remote problem"
date: 2008-05-17
forum: Mythbuntu
---

### Post by jfenton78 on 2008-05-17
I've tried for two day to get my Antec fusion V2 IR working with my Hauppauge MCE remote (the one with the my favorites buttons). Here's my hardware and such:

Antec Fusion V2 case with VFD/IR/Knob
Mythbuntu 8.04
Gigabyte GA-73PVM-S2H
1TB Seagate drive
Hauppauge PVR-500
Firewire connection to Motorola DCT-6200 STB

I've followed almost all directions from a search of antec fusion related to IR problems and no luck. When I do 'lsusb' I see the Soundgraph imon as Bus 001 Device 004. Running 'ls -a /dev/lirc*' shows /dev/lirc0 and /dev/lircd. So as far as I can tell I have only one device. I've tried to create my own lircd.conf for my remote but the irrecord is giving me problems. I tried running 'mode2 -d /dev/lirc0' and it put out continous information without any button presses. So I think something else has control of lirc0. My VFD is working fine with the exception of occational text glitches. What can I do to track down the problem and get my IR working? 

In originally setting up my VFD/IR is used MCC and selected the Soundgraph imon pad vfd/ir and generate key bindings. Thanks for the help.

jf

---

### Post by jfenton78 on 2008-05-18
Bumped to give an update. Well still no luck with the Antec Fusion built in IR. Recently I tried installing the MCE Remote and IR receiver. Although it did not work with irw or Myth, the reciever is receiving command as verified by mode2. I think that the hardware is still specified to a different device. I'm going to try changing the hardware.conf to the proper lirc device. 

If anyone has info on why the built-in IR is not receiving let me know. Thanks.

jf

---

### Post by ScratchyBoy on 2008-08-12
Hello, on not too much of a random question as I have the same hardware Antec Fusion case and giga-byte motherboard.  I've installed XP MCE 2005 and I'm having trouble getting the audio out through the HDMI cable into my TV.  It used to work but now doesnt, so I'm thinking a driver has messed things up it bit.  All the volume controls seem to work just no sound, also interestingly the SPDIF audio mixer volume scale seems to be disabled.

Another interesting point is that when the computer first fired up, I got a message saying that an HD audio device wasn't installed correctly, that's when the volume control on the front of the case didn't work but the sound output did.  But since this problems been corrected no sound is omitted.

I've updated all drivers to the latest version and tried all that I can think of so it anyones got anymore suggestion then please can they reply.

Thanks

---

