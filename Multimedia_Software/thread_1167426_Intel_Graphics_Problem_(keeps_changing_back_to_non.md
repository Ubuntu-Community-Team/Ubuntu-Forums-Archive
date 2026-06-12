---
title: "Intel Graphics Problem (keeps changing back to non-working driver)"
date: 2009-05-22
forum: Multimedia Software
---

### Post by KFwLsKvVAs on 2009-05-22
Hello,

I have been having an issue with my graphics drivers getting screwed up when I plug in my computer to my tv with a vga cable.  Before upgrading, it worked fine, mirrored both screens and didn't have to mess with resolution on either of them.  Now, it detects both monitors (laptop and tv), sets the television resolution for both of them, and i have to change it back when I unplug it from the tv.  that's fine and all, but now sometimes when i unplug it and change the resolution back to normal, my video drivers seem to be not working anymore (no desktop effects, transparency, etc...).  I've had this happen before and the only way to fix it was to revert to the old drivers, then replace them with the new intel ones again (and it took several times of doing this for it to actually work).  So I'm wondering if there is some way to just fix this driver problem thing without reinstalling the old intel drivers, and then reinstalling the new ones, like maybe just something that will make it recognize that the new ones are already there.  

here's this:
bonez@darkgrave:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0a:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


anything other info needed I can supply, I'll be here all night.

---

### Post by KFwLsKvVAs on 2009-05-23
Really anybody have any ideas?  I could use some help at least figuring out why it keeps doing this...

---

### Post by pytheas22 on 2009-05-23
It may help to [revert to the 2.4 driver]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").  Reboot for changes to take effect.

If that doesn't solve the problem, please explain what you mean by reverting to the "old drivers," and then replacing them with the "new Intel ones."  Do you mean that you switch to the failsafe vesa driver, or to the i810 driver instead of 'intel', or something else?  By default, there's only one version of the Intel graphics driver in Jaunty.

---

