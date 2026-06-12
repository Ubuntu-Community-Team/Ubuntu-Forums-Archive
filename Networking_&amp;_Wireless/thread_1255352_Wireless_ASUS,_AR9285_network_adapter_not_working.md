---
title: "Wireless ASUS, AR9285 network adapter not working"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Unzoomed on 2009-09-01
Hello there

I installed ubuntu for the first time today and most things is actually going quite well. There is just one thing that I can't seem to get working. My wireless network card.

I've been googeling for a while and tried some different thing but still not working.

**lspci **gives me:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```[B]iwconfig
[/B]```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```[B]
iwlist scan[/B]
```
lo         Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


```**sudo /etc/init.d/networking restart**
```
 * Reconfiguring network interfaces...                                   [ OK ] 

```On my laptop I also have that little wireless network lamp that is supposed to be lit but it's not. I've tried to use the "Fn" + F2(wireless on/off) but with no luck, the computer doesn't even respond on it but all other "Fn" combinations work well.

I've tried the following thing to fix it:
apt-get install linux-backports-modules-$(uname -r)
when I do this I get an error that in the end says "Are you root?"
I saw somewhere that sudo -i sent me to root so I tried that
and when I do this and then apt-get install linux-backports-modules-$(uname -r) again my ubuntu installs something. I have rebooted several times and still doesn't work.


Please tell me if you want any more information.
Thanks in advance
//Unzoomed

---

### Post by Paul7777 on 2009-09-01
Unzoomed...You are not alone, I have been working on installing a Linux system for 3 months now. I have lost my O/S 2 times through experimenting.

I really like Linux. I finally decided on the Wubi installation of Ubuntu. I did the upgrade and " poof " no wifi. It dies in both Windows Vista and Ubuntu. So I reinstall and do not do an update. It lasted less than 3 hours. I have backups of drive "C" and have done that twice in 24 hours. 

I am now reading that the WIFI needs to be upgraded to something. I have an Acer Aspire 5100. 

I hope to get this resolved. I read the forums ( Lurker ). Most of the Language might as well be French. There must be an easy solution. I really want to be able to use Ubuntu. I also need Windows, as much of our company applications require it. 

I am not giving up.......Yet

---

