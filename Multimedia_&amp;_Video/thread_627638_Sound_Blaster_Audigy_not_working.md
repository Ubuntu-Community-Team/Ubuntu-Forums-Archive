---
title: "Sound Blaster Audigy not working"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by Dradien on 2007-11-30
Hello.  I just recently installed Ubuntu 7.10.  Everything is going well, except for my sound.  MY onboard sound is gimped, and my Audigy don;t work:(.

When I do lspci, I get....

.....
02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
02:0a.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
.......

But when I type aplay -l. I get....

....**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
.......
Not there.  Anyone able to help?  Im pretty new, so I have no real clue how I would go about getting and installing a driver for this card.

Thanks!

---

### Post by Dradien on 2007-11-30
No dice, anyone?

---

### Post by linuxwizard on 2007-11-30
Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by Chudilo on 2007-11-30
Did you upgrade to Gutsy or is this a new install?

---

### Post by Chudilo on 2007-11-30
> **linuxwizard said:**
> Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

Wizard... he doesn't have the audigy listed in play devices so it's not the switches.

---

### Post by Dradien on 2007-11-30
Totally new install on a brand new 160 Gig Drive.

---

### Post by veg_meister on 2007-12-01
Hi there.

I'm a newbie - this is my first install of Linux,

I had exactly the same problem - and unchecking the Audigy Analog/Digital Output Jack fixed the problem - thanks a million.

Veg_Meister

---

### Post by linuxwizard on 2007-12-01
Hi veg_meister
Welcome to the Ubuntu Forum. Noticed that it is your first post. Glad to hear that the info helped you with your sound issue.

---

### Post by tad1073 on 2007-12-13
I am having the same problem. I have been a M$ user since I can remember and no nothing about linux. I know what a command prompt is or a terminal, as linux refers to it, but I don't know format or linux commands.

---

