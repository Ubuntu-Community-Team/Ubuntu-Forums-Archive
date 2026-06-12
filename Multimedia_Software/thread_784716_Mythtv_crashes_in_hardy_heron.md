---
title: "Mythtv crashes in hardy heron"
date: 2008-05-06
forum: Multimedia Software
---

### Post by dcallagh on 2008-05-06
Hi,

Wondering if anyone else has seen this or is it just me?

Just installed Ubuntu via WUBI on a Medion PC. This is basically my  home media PC and normally runs my TV under powercinema. 
Unfortunately mythtv crashes with a segfault everytime I press the watch tv button in the myth frontend. 

DVB card is medions with a phillips chipset and is detected ok by the backend.
Video card is ATI radeon.
3Ghz CPU
1 Gb ram
250Gb WD SATA drive

I have successfully installed the backend using the DVB card and used 'scan' to get the channel information.

Notes:

Am trialling this to see if I can at last replace the M$ solution with something linux. 

Ubuntu is gaining a reputation as an easy to install and use linux, so thought I'd give it a go.

Ubuntu installed ok, although the screen works only if I boot to Ubuntu ONLY after booting to windows, if I turn off the PC and boot straight to Ubuntu, it fails to boot (comes up in an ash prompt). This may have something to do with my problem?

Is Hardy Heron a production release or is it still beta?

---

### Post by John L on 2008-05-07
Hi dcallagh

I'm afraid I can't help you but I'm interested in the fact that any program on Ubuntu recognised the medion dvb tuner.  I have a medion pc (md8830) with a dual boot set up with both vista and hardy (direct install) running via grub.  Hardy is now a full fledged release and so far is very stable on my machine. 

I've tried many different programs from kaffiene, vlc to tvviewer etc and nothing recognised the dvb card.  When you say its medion card with a philips chipset I'm wondering is it the "creative" version of the card?  

I've managed to do most things that I need to do in Ubuntu but setting up the tv card has got me stumped.

John

---

### Post by kansei on 2008-06-18
Could you provide more info other than just "segfault"? Run mythfrontend from a terminal window (sounds like you are if you know it was a segfault) and paste anything that looks relevant when it crashes.

I'm having this problem as well after installing mythbuntu 8.04 but I'm kinda thinking it was due to the fact that there were two sound cards in the system. I got it working once but whatever changes I made didn't persist.

I know there were significant audio architecture changes between 7.10 and 8.04, so it wouldn't shock me that some default options are causing trouble with very specific hardware setups.

If I find a solution I'll post it here or link you to it.

---

