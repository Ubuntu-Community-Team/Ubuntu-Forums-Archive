---
title: "PVR 350 TV output permission problems (multi-seat Myth box)"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by madrivereric on 2007-08-24
Here is my system in a nutshell:

 ubuntu 7.04; AMD64 X2 4600+; M2NBP-VM CSM motherboard w/ Nvida Quadro onboard GPU; PVR-150 & PVR-350 video cards; PS/2 keyboard & mouse; NextGeneration Home Products RF remote extender connected to the serial port via homebrew circuit & LIRC.

The system is configured to have two seats.   One seat is my 'normal' computer and uses the keyboard, mouse and onboard graphics (my 'console').  The other seat ('PVR' seat) is my MythTV video server which uses the PVR-350's video output and the LIRC remote.  I've created a dvr user account which is automatically logged in on the video server seat and have the .gnomerc setup to launch the MythTV frontend.  The video out of the PVR is connected to a RF-modulator & amplifier to back feed the cable in the house (there's a filter trap to keep the cable company happy).  This way I can watch my MythTV on any TV in the house and the single computer lives in the basement office.   That is the plan anyways.  I'm 98% there...

When I run MythTV from my primary user account, I correctly get the video/audio out through the PVR-350 as desired so I know the hardware all works and I've worked through all of the many IVTV oh-by-the-ways (a BIG THANK YOU to the FAQ writers!!!).  I initially installed the Myth program (and most everything) as my primary user.

When I run MythTV from the PVR seat, the X-display video works, the MythTV GUI works and I can see the displayed video; however, the audio comes through the computer's speakers, not through the PVR-350's audio out.  (yes, the 'use the PVR-350 audio out' box is checked).  

When I kill the dvr's login on the PVR seat and then login on the console seat as the dvr user, the MythTV GUI runs on the monitor as expected, but when I watch TV or a recording, the output appears on the monitor/computer speakers instead of the PVR-350's output.   (yes, the same use PVR output settings are still set to the same values as when I'm running as my primary user account).

I'm guessing that some permission someplace is not set to allow the dvr user to access the needed something with the PVR-350 and so Myth defaults to the monitor/computer speakers.

I've tried using the gnome users/groups to give the dvr account all privileges and edited /etc/group to place the dvr account in the same groups that my primary account is in (except for the lpr group).  No luck.

Does anyone have any suggestions as to where to look to correct this presumed permissions problem?

Thanks!

Eric

---

### Post by madrivereric on 2007-08-24
heh... a reboot solved things.  I think I corrected the group permissions, but forgot to relogin...

A few more clean up items and then I'll put together a howto posting since there were many other folks asking how to build the same type of system...

---

