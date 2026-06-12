---
title: "No restricted video drivers work"
date: 2010-01-21
forum: Multimedia Software
---

### Post by dyoung418 on 2010-01-21
I have a strange problem that has really stumped me.  When I load restricted video drivers, my display goes blank after the initial boot messages.  The really odd thing is that I've tried this with 2 different video card (one nvidia and one ATI) and I've tried swapping monitors and cables -- I get the same problem every time.

Here are the specifics:  I'm running a fresh install of Ubuntu 9.10.  My motherboard (ASUS M2NPV-VM) has an onboard NVIDIA GeForce 6150 chipset.  The fresh install works and displays fine but of course doesn't have any of the 3d accelerator features.  After the first boot of the fresh install, I am given the message that restricted drivers are available.  If I download and install them, upon reboot I can see the POST messages and an initial Ubuntu logo, but then the screen goes black and I never see the login screen (although I suspect it is there).  I have also tried downloading the NVIDIA drivers from their website, but I get the same problem.

I thought that perhaps the accelerated graphics portion of my NVIDIA chipset was faulty, so I bought a graphics card for the PCI-E slot -- a VisionTek ATI Radeon HD 4650.  I also re-installed Ubuntu fresh.  I get the same exact scenario.  Initial boot without accelerated graphics works fine -- once I install the restricted driver (now fglrx), I get a blank screen after initial POST and ubuntu logo.

I even changed out the monitor and cable, but that didn't change anything.

Does anyone have any ideas?

---

### Post by LuridCinema on 2010-01-21
Can you shut off the onboard video in the bios / startup ? mebbe that's what is causing the prob.. usually the software see the add on card and works.

---

### Post by dyoung418 on 2010-01-21
When I plugged in the video card, I disabled the onboard video chipset in the bios settings.  The card works when first installed, just not when I try to enable the restricted driver.

---

