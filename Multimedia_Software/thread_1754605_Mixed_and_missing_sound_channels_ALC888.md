---
title: "Mixed and missing sound channels ALC888"
date: 2011-05-10
forum: Multimedia Software
---

### Post by OldBastard on 2011-05-10
Hi all. I am still an Ubuntu/Linux newbie and most of the times when I had a problem I was able to find a solution somewhere but not this time. I have upgraded to Ubuntu 11.04 from 10.04 a few days ago and I have just noticed problem with my sound. I have integrated nVidia sound card:
> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and the problem is that rear channels doesn't work and rest of them are mixed, i.e.:
I open Sound Preferences and start speaker test:
front left - plays centre speaker
front right - seems ok
centre - plays rear left speaker
subwoofer - plays rear right speaker
rear left and right - both silent

Now, I have been looking for a solution but no luck. I have tried reinstalling ALSA as per that sticky Solution thread, I have edited "daemon.conf", checked alsamixer and still nothing. If anyone have any ideas, please share. Thanks

---

### Post by lidex on 2011-05-10
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by OldBastard on 2011-05-11
Hi. Thanks for reply. Here is the link:
[http://www.alsa-project.org/db/?f=b0de8c763728295912b13337c3229dce80415860](http://www.alsa-project.org/db/?f=b0de8c763728295912b13337c3229dce80415860)
Thanks

---

### Post by lidex on 2011-05-11
I'm not sure daemon.conf is the one you want to edit - thought it was default.pa in /etc/pulse/ but I've been wrong before.

What is the make and model of this machine or if assembled, the MB?

---

### Post by OldBastard on 2011-05-11
Hi. My motherboard is Gigabyte GA-M57SLI-S4
High Definition Audio:
Audio Controller Type    nVIDIA MCP55
Codec Name                 Realtek ALC888
I can't really do much more now as I can't even log in to system:confused: I get to log in screen and get stuck there as nothing happens when I click my user name. I can go to terminal and log in there but I can't run GUI...:( Damn, sometimes it can be so annoying

---

### Post by lidex on 2011-05-11
Did you try the startx command in console after login?

---

### Post by OldBastard on 2011-05-11
Yes, it says then "server error" and "server already running"...

---

### Post by lidex on 2011-05-11
Hmm. You might try booting into another kernel. Some known issues here:
[http://ubuntuforums.org/showthread.php?t=1749312](http://ubuntuforums.org/showthread.php?t=1749312)

---

### Post by OldBastard on 2011-05-12
Ok, I wasn't able to log in properly so I reinstalled Ubuntu but that made it even worse. So then I did clean install and now all is ok including audio:) So thanks a lot guys, I'm ok now

EDIT: I would edit my 1st post to change [ubuntu] to [SOLVED] but I dunno how...

---

### Post by lidex on 2011-05-12
So a glitchy install then. You can mark the thread solved using 'Thread Tools' up top.

---

### Post by OldBastard on 2011-05-12
Thanks again. Lol seriously, I didn't expect that the solution for Linux problem will be format and reinstall... :D

---

### Post by lidex on 2011-05-12
Yeah, I feel you but sometimes it's just not a good install or cruft from previous install mucks things up.

---

