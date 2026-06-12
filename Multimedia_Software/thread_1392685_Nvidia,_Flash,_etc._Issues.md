---
title: "Nvidia, Flash, etc. Issues?"
date: 2010-01-28
forum: Multimedia Software
---

### Post by tlatseg on 2010-01-28
I am relatively new to Ubuntu, only using extensively for a month after my latest XP crash, and had been quite pleased with the performance until everything seemed to go wrong yesterday. 

TF2 was the first to crash, assumed it was because Steam had updated during the day and that this Wine version (1.1.31 with PulseAudio) was glitching. When trying again the game would work for 10-20 minutes before crashing, no errors were reported each time. Today the program will not even open.

Next was Hulu, which others have mentioned worked fine at small setting, but was choppy at fullscreen. The same was true for YouTube and Google Video. Today Hulu is working at fullscreen, but displays the occasional horizontal fragment. Firefox crashes whenever Youtube is switched to fullscreen, this problem did not occur last night. Google Chrome displays the following error: "The following plug-in has crashed: /usr/lib/flashplugin-installer/libflasplayer.so" 

Recommendations that I have followed so far:

1. Update the Nvidia driver, however, this failed displaying the following message:

E: /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa4_i386.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so.185.18.36', which is also in package nvidia-185-libvdpau 0

2. Uninstall and then reinstall Adobe Flash, same problems.

I will continue to browse the forum for related topics and fixes, but any further information, advice or redirection to other threads would be helpful.

Is there a possibility that this may be a hardware rather than software problem, and is there a program available for Ubuntu which can test things like graphics card functionality and performance?

Thanks in advance.

Here is my Sysinfo, if pertinent:

Ubuntu 9.10 (karmic)
2.28.1 (Ubuntu 2009-11-03)
2.6.31-17-generic-pae (#54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009)
4.4.1 (i486-linux-gnu)
AMD Athlon(tm) 7750 Dual-Core Processor 1350.000 MHz
NVIDIA GeForce 9600 GT PCI-E 16x 512 MB 650 MHz
NVIDIA UNIX x86 Kernel Module  185.18.36

---

