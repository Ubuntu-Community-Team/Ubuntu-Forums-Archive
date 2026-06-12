---
title: "Cannot change resolution or refresh rate"
date: 2008-06-25
forum: Multimedia Software
---

### Post by Rhapsody on 2008-06-25
This is a nasty problem that I'm at a loss to explain or solve. The computer in question uses integrated graphics (GeForce6-class, no other information), connected to a Samsung SyncMaster 793s, and is running Ubuntu 8.04.

The problem is that the resolution and refresh rate are at 800x600 @ 60Hz and nothing will change that. I know for an absolute fact that the PC can handle 1024x768 @ 85Hz but nothing will actually set the PC to that. I tried "gksudo displayconfig-gtk", changed the monitor to match what I've got, changed the resolution and refresh rate to what I wanted, applied it, and nothing happened. Nothing whatsoever. My previously foolproof solution of using "dpkg-reconfigure xserver-xorg" (which worked on Kubuntu 7.10) also failed as it no longer asks me any questions about the monitor, only the keyboard.

It seems my only option left is to poke around in xorg.conf until I can force it to use the settings I want, but is there anything I missed in this?

---

### Post by logos34 on 2008-06-25
Is the Nvidia graphics driver enabled?

system>admin>hardware drivers

then,

sudo nvidia-settings

you may need to get it with sudo apt-get install nvidia-settings)

---

### Post by Pjotr123 on 2008-06-25
1. sudo apt-get install nvidia-settings

2. gksudo nvidia-settings

That should do the job.  :-)

---

