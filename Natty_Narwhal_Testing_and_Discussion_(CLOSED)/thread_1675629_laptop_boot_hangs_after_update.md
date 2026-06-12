---
title: "laptop boot hangs after update"
date: 2011-01-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Genesius on 2011-01-25
Yeah, the chance you take running an Alpha build. . .

Acer TravelMate 6460 laptop. When I boot, it gets as far as Plymouth, then the screen flashes and goes blank. Reboot into recovery mode and try to run failsafex, the screen flashes and goes blank.Drop to root prompt, and even hardwired to my router I can't get networking. Every few minutes I get a message

```
tpm_tis 00:0b: tpm_transmit: tpm_send: error -62 
```

Is it salvageable? Or is it time to nuke the hard drive and start from scratch. Gotta start looking for instructions for mounting the HD from a LiveCD so I can recover my Firefox settings. . .

---

### Post by Harry33 on 2011-01-26
> **Genesius said:**
> Yeah, the chance you take running an Alpha build. . .

Acer TravelMate 6460 laptop. When I boot, it gets as far as Plymouth, then the screen flashes and goes blank. Reboot into recovery mode and try to run failsafex, the screen flashes and goes blank.Drop to root prompt, and even hardwired to my router I can't get networking. Every few minutes I get a message

```
tpm_tis 00:0b: tpm_transmit: tpm_send: error -62 
```

Is it salvageable? Or is it time to nuke the hard drive and start from scratch. Gotta start looking for instructions for mounting the HD from a LiveCD so I can recover my Firefox settings. . .

What update are you talking about (in the title)?
Do you have xorg-edgers PPA in sources.list?

---

### Post by Genesius on 2011-01-26
Regular update manager update, on Monday if I remember correctly. Yes, I have xorg-edgers in my sources.list

---

### Post by Harry33 on 2011-01-26
> **Genesius said:**
> Regular update manager update, on Monday if I remember correctly. Yes, I have xorg-edgers in my sources.list

Having xorg-edgers in sources.list is ATM not a good idea.
There is a xserver ABI (server version 1.10) change ahead in Natty, but this has already been uploaded a few days ago in edgers PPA. So your issue might just be due to that.
Also Nattys libdrm and libgl1-mesa packages have been changed along with plymouth packages. The package libdrm-nouveau1 is now libdrm-nouveau1a.

If you have nvidia binary drivers (nvidia-current) in use, that is the reason for the breakage.

---

### Post by Genesius on 2011-01-26
Nope, the laptop's got an ATI Radeon card.

Any way I can convince my machine to connect to my home network wired? The hardware's fine - if I boot with a live CD I can get online with no problem but whatever borked my display also borked networking. Doesn't matter if I go to the root prompt or netroot from recovery mode, when I try to run apt-get update it can't resolve the server names.If I can get it online, I can just keep running daily updates until it installs the package it needs.

---

### Post by kyleabaker on 2011-01-26
I've got an nvidia card, with no restricted drivers installed and my system hangs on boot as well. I don't see a specific error though. How can I tell where the actual problem is? I am able to access the console though.

---

### Post by SevenMachines on 2011-01-27
xserver-xorg-video-intel 2:2.14.0-1ubuntu2 is causing a blank screen hang here on attempted vt switch on gdm or startx. Workaround by switching to vesa or downgrading to working version
[http://ie.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.13.901-2ubuntu3_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.13.901-2ubuntu3_i386.deb)

---

### Post by antoniomiguel on 2011-01-27
Try to update again, a new patch has just been issued..

---

### Post by kyleabaker on 2011-01-27
I saw an update for xserver-xorg-video-intel within the last hour or so. Try running updates and reboot. For me it was, xserver-xorg-video-nouveau. Its all working again for me now.

---

### Post by SevenMachines on 2011-01-27
Indeed xserver-xorg-driver-intel 2:2.14.0-1ubuntu2 fixes boot for me, always nice when you get up in the morning and someones fixed everything for you :)

---

### Post by Genesius on 2011-01-27
Yay! Had to run "ifconfig eth0" to get my Ethernet running, then the update fixed the display problem.

---

