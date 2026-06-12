---
title: "Atheros AR8132 ethernet no longer detected?"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by imhumn on 2010-03-01
Hello, all.  I have an absolutely bizarre hardware issue (concerning the Atheros AR8132 PCI-E Fast Ethernet Controller) that has been giving me quite a bit of grief for a while, and having completely hit a wall on this one, I'm reaching out for help.

I'm a reasonably-experienced Linux user of several years, and have been running Ubuntu 9.10 on an Acer AOD250 netbook for several months out.  I know that this model has wireless issues out-of-the-box (easily fixed), but it did not have any noticeable ethernet issues.  That is, until I attempted an installation of Arch Linux.

During the Arch Linux installation, the ethernet card was initially detected, but unable to be used (because of a bad module in the kernel released with the installer).  As I didn't know the fix for this at the time, I decided to reinstall Ubuntu 9.10.  This time, however, the system failed to recognize the wired ethernet whatsoever.  Instead, the external activity lights for the port (green and orange) are ALWAYS on, yet the device doesn't function.

I have done a successful install of the latest drivers directly from Atheros for the device and have them automatically loading with the kernel during boot, but as the device isn't recognized, the drivers aren't doing any good.

Relevant information:
```
root@niobium:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```Judging by the name, the Atheros AR8123 uses a PCI-E (express) adapter.  Especially curious is the following section of the output:
```
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
```I suspect that my "lost" ethernet card may be on the mysteriously-absent Port 3.

My knowledge of hardware manipulation from the terminal is very limited, and I have no idea where to go from here, so any help will be greatly appreciated.

---

### Post by imhumn on 2010-03-01
It is perhaps worth mentioning that I have the newest Acer BIOS version for this model (which is extremely limited in capabilities) and that the two ethernet port lights turn on and stay on all the time while the computer is connected to its AC adapter.

Very strange...

---

### Post by datajock on 2010-03-26
I have seen other messages regarding similar situations and thought I would help maybe clarify what is going on.

With many new network interface ports there is a *feature* for what I am going to call "wakeup from the network". This means that even when the computer is turned off that the network interface must **still have power**. So if you manage to get the NIC in some kind of hung state, the only way to clear it out is to **unplug the power** from the entire system.

Since here we are dealing with notebook (or netbook) computers, this means you **also have to remove the battery** or it will not actually have power removed from the NIC.

This is something to keep in mind when ever you are dealing with a problem with a network interface that seems to "disappear" from the system or hangs and a reboot or even power cycle of the system doesn't seem to clear the issue.

Hope that helps someone reading this down the road.
DJ

---

### Post by imhumn on 2010-03-26
datajock,

I appreciate the response, and that's definitely something I considered.  I still feel that if the NIC were in some sort of hung state in preparation for a LAN wakeup, that either Windows or Linux would be able to detect the adapter.

I actually removed the battery and AC adapter from the netbook and left them separate for five days to completely discharge the electronics, and there was no change in the system.  Since posting this, it appears there's two blown LAN ports on my wireless router and a burned-out CAT5 cable, so I suspect that the NIC got burned out by an electrical event at this point (either router to netbook or vice versa), since everything I've tried so far to troubleshoot this issue has failed.

Thanks for your ideas though!

---

