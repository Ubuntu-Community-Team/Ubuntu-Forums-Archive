---
title: "Maverick restarts instead of shutdown"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by argab on 2010-10-02
I just tried Maverick RC and found this bug. If I try to shutdown my notebook, everything seems to go smoothly, but right after the computer shuts down it restarts immediately. Tried on Ubuntu and Kubuntu 10.10 RC, and this is an issue on the LiveCD-s as well, not just after installation.
Any ideas what can cause this? 10.04.1 and Win7 works fine, and there are no ACPI settings available on the bios.

---

### Post by thiebaude on 2010-10-02
I have had that problem since Ubuntu 10.04, When I go shutdown my computer it will restart, I have a bug number on it, but I don't remember what the bug number was.Ever since plymouth was implemented I have had that proble, but I cant prove if plymouth is causing it.I want to yes it is but again ,I don't know.I have Amd dual core.32bit or 64bit opteron 165 processor.

---

### Post by zaphod777 on 2010-10-03
you should probably report it as a bug. It works fine for me though.

You might want to try 
```
sudo shutdown -h now
```
from the terminal and see if you get the same result. You don't have wake from LAN or anything enabled in the BIOS do you?

---

### Post by argab on 2010-10-03
I tried
```
sudo shutdown -h now
```
but I had the same result.
I don't have a wake on LAN setting, the only one slightly related is Network Boot, but it's disabled.

I reported this on launchpad and attached ```
lspci -v
```. Any suggestions what else should I attach?

---

### Post by zaphod777 on 2010-10-03
You may also want to check the power management settings in the BIOS and check to see if there is a bios update available. 

Other than that the folks on LaunchPad will probably tell you what other commands to post the results of.

---

### Post by argab on 2010-10-03
There are no power management settings available in the bios and I already have the latest version from january 2010.
I can only enable/disable network boot, quiet boot and acer's d2d recovery, switch the sata controller between IDE emulation and AHCI, and enable/disable the integrated Radeon HD3200 for Hybrid Crossfire.

---

