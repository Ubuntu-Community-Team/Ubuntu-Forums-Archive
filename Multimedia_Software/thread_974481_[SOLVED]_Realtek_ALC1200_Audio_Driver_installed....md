---
title: "[SOLVED] Realtek ALC1200 Audio Driver installed... now no sound"
date: 2008-11-07
forum: Multimedia Software
---

### Post by heatpumpcontrol on 2008-11-07
I have the P5Q PRO board which has the Realtek ALC1200 Audio and under this command I get:

```
sudo lshw -class sound
 *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

The audio was working but I hosed it when I installed the realtek-lnux-audiopack-5.01 I downloaded from Asus. I am running the 
Linux 2.6.27 Server Kernel as I have 4GB ram. I reinstalled the Kernel to no avail. I had it all set up with Pulse Audio before so I had multiple sound inputs... that were working. :(

I rebooted into Kernel 2.6.21 Server and the sound shows it's using Realtek ALC888(OSS Mixer) in Sounds and it worked but it won't under 2.6.27 server, the Mixer Tracks is blank in Sounds.

Any suggestions?

Ibex installed
Thx

---

### Post by heatpumpcontrol on 2008-11-07
OK Solved!!!!

I did the following...
1. Uninstalled and reinstalled the following:
 [LIST]
[*]linux-backports-modules-intrepid-server
[*]linux-headers-server
[*]linux-image-2..6.27-7-server
[*]linux-image-server
[*]linux-restricted-modules-2.6.27-7-server
[/LIST]

rebooted and everything started to work except my boot up and login sound are now gone but... hey I can deal with that...

---

### Post by lukedupree on 2009-01-25
So how do you uninstall and re install the components you listed?

---

### Post by djamu on 2009-05-14
I posted a very easy proper fix here 

> [http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

---

