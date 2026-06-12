---
title: "[SOLVED] low res only after new video card install"
date: 2008-07-08
forum: Multimedia Software
---

### Post by ymp on 2008-07-08
Using Ubuntu 8.04,
Have a widescreen LCD plugged into the onboard video controller.
Everything was working fine until I installed a PCI video card for a second monitor and am now stuck on a 800x600 resolution.
Installing the card seems to have wiped out my previous XORG.
I've removed the card, and still only low res.
I have tried configuration through Other > Screens & Graphics, however I cannot seem to change the card driver from Generic VESA to NVIDIA, and although I can choose a higher res, when tested are unreadable.
Any suggestions on how to fix this problem welcome, 
I've looked through the documentation, and threads but can't seem to find anything workable.

---

### Post by overdrank on 2008-07-08
> **ymp said:**
> Using Ubuntu 8.04,
Have a widescreen LCD plugged into the onboard video controller.
Everything was working fine until I installed a PCI video card for a second monitor and am now stuck on a 800x600 resolution.
Installing the card seems to have wiped out my previous XORG.
I've removed the card, and still only low res.
I have tried configuration through Other > Screens & Graphics, however I cannot seem to change the card driver from Generic VESA to NVIDIA, and although I can choose a higher res, when tested are unreadable.
Any suggestions on how to fix this problem welcome, 
I've looked through the documentation, and threads but can't seem to find anything workable.

Hi and you can try and reboot in to recovery mode and use the xfix option and this should correct the issue.

---

### Post by ymp on 2008-07-08
thanks, but that did not help,
I have tried using the reconfiguration utility to reinstall Nvidia driver, but it always reinstalls the generic VESA, and 600x800, despite about 10 restarts after configuration it just doesn't accept it, very frustrating

---

### Post by overdrank on 2008-07-08
> **ymp said:**
> thanks, but that did not help,
I have tried using the reconfiguration utility to reinstall Nvidia driver, but it always reinstalls the generic VESA, and 600x800, despite about 10 restarts after configuration it just doesn't accept it, very frustrating

Hi and could you give us some specs on the system like memory and graphics?

---

### Post by ymp on 2008-07-08
I have resolved the screen problem by using EnvyNG to install the Nvidia driver. This has restored my screen to previous resolution.
Now, I will have to figure out how to install the card without wiping out my XORG and setting up a dual monitor system

---

### Post by overdrank on 2008-07-08
> **ymp said:**
> I have resolved the screen problem by using EnvyNG to install the Nvidia driver. This has restored my screen to previous resolution.
Now, I will have to figure out how to install the card without wiping out my XORG and setting up a dual monitor system

If you have a onboard nvidia graphics along with the additional nvidia graphics you may be better off disabling the onboard graphics and just using the additional card for the dual monitors ( if the graphics card is dual head. Good luck!

---

