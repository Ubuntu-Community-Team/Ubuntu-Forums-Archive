---
title: "PVR-150 MCE LP newbie seeking help"
date: 2007-12-16
forum: Mythbuntu
---

### Post by ndorf on 2007-12-16
Hope somebody can help...I'm not exactly a Linux newbie but I'm quite rusty nowadays and I got myself in over my head.

I wanted to build a MythTv box for a bedroom armoire, so the case had to be slim. I have a DirecTV Hughes GAEB0 recever that feeds Svideo into my capture card. There is no data port so I will need to use an IR blastter.

This  dictated my choice of components:

Slim case with 300W ps
Hauppauge PVR-150 MCE Low Profile (which I fear may require different drivers than the regular height 150?):confused:
(to get a low profile version it only comes in MCE version no remote)
Dell Media Center Edition 2005 remote (RC6) which comes with the bean bag IR receiver and an IR blaster that plugs into the back of the bean bag.
Jaton AGP 128Mb Nvidia 5200 chipset with SVideo out
2.8Ghz Pentium 4 with 1Gb RAM, 100Gb HDD
Atheros-baed Wireless G card (working fine with native drivers)

TV is a 27" Magnavox with Svideo input std def nothing spectacular

Here are the problems

1) The video signal to the TV is somewhat "trapezoidal" shaped, that is, the left-edge curves a little bit from top to bottom. Could not find a remedy on the TV, or nvidia-settings, or Mythtv playback menu (overscan does not do the trick)

2) Crude pixelation (is it called tearing) and chirping audio off and on, and seems to depend upon what station I have tuned to.  This is my biggest problem right now. I've plowed through many forums and threads and so far cannot find the answer.

Already changed the default recording profile resolutions to 720x480 in MythTV and also did so from the command line with v4l2-ctl command.


3) Although the remote works for basic Mythtv functions, I just can seem to make the "tethered" blaster work to change channels. I found an lirc.conf settings file for my GAEB0 and appended those commands to the end of my existing lirc.conf but to no avail. I also found a change_channel.sh script but it doesn't seem to be working either.

I'm hoping to get this working without having to download and compile source...

Thanks much to anyone who can help.

---

### Post by ndorf on 2008-01-15
OK, lots of people read this  (thanks for reading) but no ideas.

So in the spirit of helping others who may encounter similar problems:

1) Never did figure out the trapezoidal screen image. Decided to just live with it.

2) Chirping and pixelation / tearing. Looks to be a signal quality issue. I went out to the dish and found a few loose connections. The cables at the dish's LNB needed tighteniing. Two other cables run from the dish to a signal splitter (2way-->4way) and those needed tightening both going into the splitter and coming out. The cables coming out run into another splitter at the base of my house, which is the entry-point for TV service. They needed tightening as well. Apparently there was not enough signal loss to affect sending the signal from the Hughes Sat receiver into the TV, but there definitely was to send the signal first to MythTV capture card and then out to the TV.  Lesson learned.  I may wind up purchasing a signal amplifier that supports up to the 2Ghz band to further improve the signal quality. For now, problem solved.

---

### Post by ndorf on 2008-01-15
Also on the third item, got the channel change script working to blink over to the Hughes sat receiver. May have to tweak the delay a little bit.  Just a Lirc quirk I needed to work through.

---

