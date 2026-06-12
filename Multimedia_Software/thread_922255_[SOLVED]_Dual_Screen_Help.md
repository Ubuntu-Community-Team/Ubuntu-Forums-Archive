---
title: "[SOLVED] Dual Screen Help"
date: 2008-09-17
forum: Multimedia Software
---

### Post by Kanucker on 2008-09-17
The PC has an 8800GT superclocked (512mg) video card.
It comes with 2 screen outputs. One is plugged into an LCD pc monitor(24"), one is plugged into an LCD TV (32").

Works fine in Windows, but dosen't work in Ubuntu. Not sure how to go about setting up.

Any help is much appreciated.

---

### Post by chewearn on 2008-09-17
I will assumed you have nvidia restricted driver already running without issue, and just want to enable dual screen.  Nvidia has it's own configuration tool called nvidia-settings.  You should use that, instead of the Ubuntu's "Screen Resolution" utility.

Install it via Synaptic Package Manager, or run the command below:
```
sudo apt-get install nvidia-settings
```Before you begin, back-up /etc/X11/xorg.conf file, in case you messed up and need to revert.

Run nvidia-settings with root privilege:
```
gksudo nvidia-settings
```You have to decide whether to use twinview or separate X screens.  Save the changes you made to xorg.conf, by clicking "Save to x Configuration File".

Once done, you need to restart Xorg, or simply reboot for the changes to take effect.

---

### Post by Kanucker on 2008-09-19
chewearn,

Good call. I added the settings panel for Nvidia, and it works fine now. Thanks for your help.

Cheers!

---

