---
title: "Ubuntu 14.04 and fglrx for Radeon HD 7670m"
date: 2014-05-10
forum: Multimedia Software
---

### Post by bmhieserich on 2014-05-10
I've been trying to install fglrx for my Sony VAIO on Ubuntu 14.04 for a month now, with no luck.  I've tried several versions of fglrx, including the version in the repos, the latest stable version (14.10.1006) and the beta version.  It seems that something in my setup is causing the scanner to not detect my Radeon HD 7670m when installing.

When installing the fglrx version from the repos, I end up rebooting into low-graphics mode and I'm forced to uninstall it to make it work.  Even when I attempt to run something involving 3D graphics before rebooting, it comes in as a jumbled mess, meaning that version is clearly not working somewhere.  Until the dialog box pops up that says installation will not complete, there doesn't appear to be any problem indicated in the terminal.

When attempting to install other versions of fglrx, when the installer scans for an adapter, it tells me that my adapter isn't supported and that it won't install.  I run Intel/ATI dual-graphics, which makes me wonder if perhaps it's detecting the Intel card but not the Radeon HD card.  14.10.1006 was the version I downloaded from ATI's site when it asked me what I'm running, and I've done some research which says my card is supported, so I feel something's not really working here, like perhaps it could be the kernel or my version of X that's not working.

I had similar issues with installing fglrx after upgrading to 13.10 from 13.04 (where I had no trouble installing fglrx) but I found a workaround there.  Sad thing is I don't remember how I worked around it.  Further, I don't know if the workaround messed with anything having to do with Mesa or OpenGL, but the Software Updater seems to constantly be putting their packages up for updates, which makes me wonder, if they're not being updated almost daily, if perhaps the workaround blocked them from being updated.

I'm running Ubuntu 14.04 with kernel version 3.13.0-24-generic and the latest version of X to come through the repos (don't know how to find the version number).
My lspci gives me this:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] (rev ff)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 07)
03:00.1 System peripheral: Ricoh Co Ltd Device e232 (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
```

Whatever help can be offered would be greatly appreciated.  Thanks in advance!

---

### Post by robi-hipnos on 2014-05-12
I guess you bumped into the same problem as I did with HD 6370M described here: [http://ubuntuforums.org/showthread.php?t=2217632](http://ubuntuforums.org/showthread.php?t=2217632)

Still no known solution found :/

---

### Post by bmhieserich on 2014-05-16
Well, I finally was able to actually install the latest fglrx on the computer, and it still ended up in low-graphics mode with the "No supported adapters detected" message when running aticonfig and I ended up booting into low-graphics mode and uninstalling it.  So no luck with the latest ones either.

I'm trying to install it because to be honest, the open source driver is just horrible for this card when it comes to games and Steam and anything having to do with video.  I can hear my computer straining to keep up with even YouTube video on some occasions, and I can no longer play hardly any of the games I bought from Linux Steam.  When I had fglrx installed correctly even as recently as 13.10's release, everything ran fine.  Now Steam even tells me when logging in that OpenGL isn't direct rendering, and I know 3D acceleration isn't supported for my card on the open source driver.  Does anyone know if they're ever planning on putting 3D acceleration for the 7670M in the open-source driver, or if I can somehow enable it myself?  If that's possible, that may solve problems.  But right now, the open source driver for this setup just isn't working for me.

---

