---
title: "No Wireless connection after upgrade :("
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by faisalnet5 on 2009-02-05
Hi everyone, having a common problem but cannot solve it. So need help...

First of all, i installed ubuntu 7.10 and while i was installing then it was showing me some security threads was not working and every time i skipped that and tried to install. Well, after installation everything was fine, my wifi connection was great but from terminal when i was typing 'sudo apt-get update'-it was showing me as follows:

[PHP]faisal@faisal-laptop:~$ sudo apt-get update
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy/main Packages
Reading package lists... Done
[/PHP]

Then though my wifi was working so i upgraded my Ubuntu version from 7.10 to 8.04 and now having the same problem plus my wifi is not working. :(

I am seeing the small network icon in my panel and when i am clicking on it, it is showing only Wired network and Manual configuration. And also from terminal i was trying to run 'sudo apt-get undata' i fould the same problem. Below i am giving the 'lspci' output of my notebook (TOSHIBA-Satellite A135-S4527):

[PHP]faisal@faisal-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
[/PHP]

And the info of my 'ifconfig' is as follows:

[PHP]faisal@faisal-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:fc:51:ff  
          inet addr:10.10.10.101  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fefc:51ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2472910 (2.3 MB)  TX bytes:226725 (221.4 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1758 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87900 (85.8 KB)  TX bytes:87900 (85.8 KB)
[/PHP]

Can anyone please help me.....??

Regards

---

