---
title: "[SOLVED] Can't get Nvidia Binary drivers to work no matter what method I try :("
date: 2008-08-18
forum: Multimedia Software
---

### Post by jai_mantravadi on 2008-08-18
Update:
Whoops! I guess I should read the manual. It turns out for my motherboard's graphics options, PCI is not the PCI express slot, but a regular PCI slot, and PEG is the "PCI express Graphics". So, although the nv open source driver could use the graphics card, the nvidia closed source driver could not without the PCI Express being initialized as first display. PEG wasn't listed in the bios help, and I figured it was something like the ATI combined graphics with onboard chipsets (but maybe that's not part of 690G). I rebooted, re-installed using Envy, and got my 3-D accelerated desktop (and now can play games :) ).


Rest of original post below for anyone who was interested:
Good morning! 
I've been trying like crazy to get ubuntu to give me 3D acceleration, and for the life of me I can't. I've got the system listed below. First, I attempted to get Ubuntu running with the Binary ATI driver, and couldn't for the life of me. I tried every method listed in the Binary Drivers howto including Restricted Drivers Manager, Envy, and ATI's website. Every time, I get an unusable blank screen. I haven't had very much luck with ATI(AMD) in the past, so I decided to take a chance on another Nvidia card. My other Mythbox installed 3d acceleration on an old Geforce 5300 with no problems. Figuring I'd have no problems on this card (there were reviews on newegg stating others had gotten it running in Ubuntu), I attempted to install the proprietary drivers, but again, no dice. I'm posting my xorg.conf and Xorg.0.log files here in the hopes that someone can help me get my 3D acceleration working on *one* of my video cards.
Oh, by the way, I've tried an upgraded version of hardy (from Gutsy) and 2 fresh installs (1 with ATI, and 1 with Nvidia). Please help!! This card works fine with the open-source drivers, but I need 3D acceleration.

$lspci | grep -i nvidia 

gives:

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

Installation Procedure
1) I tried Restricted drivers manager, reboot.
Results: Blank screen on reboot (can switch to TTY 1/2, etc). The monitor detects a signal, but nothing is displayed on screen.

2) Tried Envy with latest drivers (automatically and manually: driver version 173.14.12), reboot.
Results: Weird Text-mode screen on bootup (all green, cursor on top). Can switch to TTY 1/2, get a blank screen when switching back to the graphics screen (similar to 1) 

3) Tried manual configuration after xfix using nvidia-xconfig, same results as #2

4-6) I tried Envy manually again after uninstalling the drivers with Envy and rebooting (same results), manually for previous driver revision (96.43.05) after uninstalling and rebooting (same results), and installing the file from Nvidia's website (NVIDIA-Linux-x86_64-173.14.12-pkg2.run), all with the same blank screen as #1, or the weird text-mode screen as #2. I decided not to keep recording the results.

Can anyone please help?! 

I've attached the xorg.conf files and the corresponding Xorg.0.log files in to the steps 1-3. I can't seem to debug what the output of the log files mean. I get something repeated a bunch of times like:


```

(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Initialized GPU GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***

```

at the end of each of my log files. I can't seem to figure out what to do next, and searching doesn't seem to reveal anyone with the same problem.

My system is:
Kubuntu 8.04.1 (Multiple Fresh installs)
GIGABYTE GA-MA69GM-S2H AM2 AMD 
4GB Adata Ram
AMD 64X2 5000+ Black Edition (not OC'd at the moment)
Video: Onboard AMD x1250 (turned off at the moment)
Then Added: ZOTAC GeForce 7300GT 256MB

---

