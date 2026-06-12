---
title: "Ubuntu 8.04 Nvidia Problem"
date: 2008-06-25
forum: Multimedia Software
---

### Post by m021998 on 2008-06-25
Hello.
  I am having a problem loading the restricted nvidia drivers on my machine.  I have a desktop machine I use mostly for web browsing, IM and music, but I would like to try out compiz.  Eventually I plan to install mythtv backend/frontend for recording.  My setup:

MSI K8N Neo4 SLI
AMD64 3500+
2x512 PC3200 RAM
MSI GeForce 8600GT 256 (PCI-E)
sata 80GB drive
LG Flatron L1920P (DVI)
2xHauppauge PVR-250 (PCI)

  I did a clean install of 8.04 with the alt disk (encrypted lvm) several times.  So far I've tried:

1.clean install, update, dist-upgrade, install restricted driver through system>admin>hardware drivers
2.clean install, system>admin>hardware drivers install
3.clean install, nvidia website drivers
4.clean install, nvidia website beta drivers
5.clean install, envyng-gtk

1-4 result in getting through the flash screen but when gdm starts, my lcd goes to sleep and the machine hangs (i can ping it, but i can't ssh in to it).  ctrl+alt+f* fails to get a video signal.
5 results in gdm trying to launch 3 times but fails, then leaves me at the x config menu where i can set desktop settings and driver.  Here I can use the nv driver and a test passes, but the nvidia driver gets green pixels at the top left and a failed to configure dialog.

I've tried various combinations with /etc/modules having nvidia and /etc/default/linux-restricted-modules-common having nv.

My /var/log/xorg.0.log has the line:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I've been searching through these forums and google for a whole day now and I can't find any more advice for what to try or what to check.  

Thanks in advance for any help.

  --paul

---

