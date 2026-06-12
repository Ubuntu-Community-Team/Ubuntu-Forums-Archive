---
title: "Wireless problems on Ubuntu 11.04"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by evrimfeyyaz on 2010-12-26
Hello everyone. I have a Samsung N210 and just installed Ubuntu. I'm new to Linux and I have some problems.

I'm using Linksys WRT110 Router. When I'm connected via ethernet cable everything's fine but when I unplug the cable and try to use wireless it's really problematic. The connection is unstable. I can use the internet for 5 minutes and then for a couple minutes it's gone and it comes back again and so on. But the thing is, it always shows that it's connected, but I can't connect to any websites. As I said, no problems with ethernet cable.

I made some research, installed Samsung-tools (and then came here to ask) and Realtek 8192E wireless driver for the latest kernel for Samsung netbooks with no luck. Also I uninstalled Network Manager and installed wicd, that didn't work either. What may be the problem?

Thanks in advance for all the suggestions.

P.S.: When I open System > About Ubuntu, it says "You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012." Why does it say 11.04? And April 2011, huh?

---

### Post by walt.smith1960 on 2010-12-26
For starters, you'll probably want to copy the result of this command:

Open a terminal windows --top left panel click Applications -> accessories -> terminal

In the resulting black box type the following 

lspci

copy & paste the resulting text

If you're using a built-in wifi, this command should come up with several lines of text.  Somewhere in that text you'll see references names like Atheros or Broadcomm or Realtek. That will be the manufacturer of your wireless chip.  Then we have a place to start but paste the entire output of lspci please.

If you were using a plug-in wifi adapter you'd use the command lsusb.  That will list all USB devices.

---

### Post by evrimfeyyaz on 2010-12-26
Ok. I did what you said, here it goes:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

---

### Post by evrimfeyyaz on 2010-12-26
I installed  linux-backports-modules-wireless-maverick-generic and everything seems fine right now.

---

### Post by afroldy on 2010-12-26
> **evrimfeyyaz said:**
> I installed  linux-backports-modules-wireless-maverick-generic and everything seems fine right now.

Could you please give more information on how you did this?

---

### Post by evrimfeyyaz on 2010-12-26
For anyone that is interested, you can use this link to download the appropriate packages:

[http://apt.ubuntu.com/p/linux-backports-modules-wireless-maverick-generic](http://apt.ubuntu.com/p/linux-backports-modules-wireless-maverick-generic)

---

### Post by walt.smith1960 on 2010-12-27
> **afroldy said:**
> Could you please give more information on how you did this?

You can do this via synaptic.  System -> administration -> synaptic package manager.
In the search box type "backports" without the " ". Check the appropriate boxes and click "apply".  That should do it.

---

### Post by ptashe on 2010-12-28
I am having a similar problem.  My wireless network is a Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01). It shows up fine and displays all the wireless networks in my area but when i click on mine and enter the password it tries to connect and then show that there is a problem with the password.  I know i typed the password in correctly, several times but no luck.  Yes, i did double check the password in my router just to make sure i was typing the correct thing.  Any ideas?

---

### Post by gseward on 2011-03-25
Running Natty 11.04 my usb wireless adapter connects, then fades out.  I have tried to follow the link to "linux-backports-modules-wireless-maverick-generic"  but I am told I am not running Ubuntu! If I try Synaptic and search for "linux-backports-modules-wireless-maverick-generic" or any part thereof I find no wireless backports. If I am using 10.10 I can get the backports either way, link or synaptic, but I don't need it there, my wireless works great in 10.10.
My adapter uses the ralink RT2870/RT3070 chipset and has worked in all versions of Ubuntu from 7.04 on, just failed in 11.04.
Any help/ideas available?

---

### Post by motang on 2011-04-02
> **gseward said:**
> Running Natty 11.04 my usb wireless adapter connects, then fades out.  I have tried to follow the link to "linux-backports-modules-wireless-maverick-generic"  but I am told I am not running Ubuntu! If I try Synaptic and search for "linux-backports-modules-wireless-maverick-generic" or any part thereof I find no wireless backports. If I am using 10.10 I can get the backports either way, link or synaptic, but I don't need it there, my wireless works great in 10.10.
My adapter uses the ralink RT2870/RT3070 chipset and has worked in all versions of Ubuntu from 7.04 on, just failed in 11.04.
Any help/ideas available?
Do you have you wifi as n? If so try turning that off and just using b/g for now, it seems to works for when I did that.

---

### Post by gseward on 2011-04-04
Do you mean set the router to broadcast in b/g only?

---

### Post by motang on 2011-04-04
Yep, that's what I mean.

---

### Post by gseward on 2011-04-04
Thanks, but no change when I change to broadcast b/g only.  I connect at a slow speed and then it gets slower yet over a few minutes.  For example it takes an hour or more to load all the repositories when trying to update. [actually it usually times out]

---

### Post by motang on 2011-04-05
Dang. :( I know the reason we are having the wifi problem is because of the kernel, hopefully with a newer release a.k.a. beta #2 this will be fixed.

---

### Post by steve1979 on 2011-04-30
hi too have the same problem on a dell laptop here is what i got from the terminal 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
steve@steve-Inspiron-1520:~$ 


im quite sure i have the drivers installed but ive been trying for days to get connected, i even double check the password etc on the router to make sure it is right, i hope u can help me as i am currently connected by a Ethernet  wire.:confused:

---

### Post by tacasi on 2011-04-30
Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

---

### Post by steve1979 on 2011-04-30
_**didnt work for me sorry!**_

---

### Post by marvincide72 on 2011-04-30
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.
thanks Tacasi. this worked for me on my Dell M1210 XPS.

---

### Post by steve1979 on 2011-05-01
ive re installed 10 4 all works fine now

---

### Post by 40twist on 2011-05-01
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

Thank You Brother!   this finally worked for me , signed up to say thank you and to have a place to go for help in the future.

---

### Post by jvhm on 2011-05-01
It worked here too!!
Thank you very much!

---

### Post by G3n1k on 2011-05-02
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

that just make my the wireless can choice but not scan the network

my laptop is lenovo 3000 G320, use broadcom BCM4312 LPPHY (use** $ sudo lspci** )
here my step

[LIST=1]
[*]remove bcmwl-kernel-source
[*]install b43-fwcutter
[*]install firmware-b43-lpphy-installer
[*]restart
[/LIST]
now i get with command
[B]$ sudo iwconfig
[/B]wirelles as wlan0, 
and can choice to activate wireless network but can't scan wireless network

so i tried to ifconfig, but the wlan0 not up

up the wlano with command
[B]$ sudo ifconfig wlan0 up
[/B]
scan the wireless network
[B]$sudo iwlist wlan0 scan
[/B]
now i get the essid, and tried connect with 
**$ sudo iwconfig** wlan0 **essid** _my_essid_ **key** _my_wireless_key_convert_from_char_to_hex_code

tried again with ifconfig and now i get the wlan0 associated with _my_essid_
but still not connect to internet 

any sugestion ?

---

### Post by randyphx on 2011-05-02
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

Hey I wanted to say thank you. I was having wifi issues also, but I did what you said by removing the "bcmwl-kernel-source" and restarted and it works great. I did not need to add the installer and the fwcutter as they were installed already. Thanks again.

---

### Post by scoobdude on 2011-05-02
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.


This worked for me after a reboot.  Thanks!!!

---

### Post by MorganJarl on 2011-05-03
Thanks! It worked for me too. Great fix! I'll link to this post from the one I created.

---

### Post by icabodffrog on 2011-05-03
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

This worked a treat with belkin wiless g network card.

---

### Post by tigeraway on 2011-05-04
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.


Thanks! This worked for me on my Dell Vostro 1500.

---

### Post by Jock1 on 2011-05-04
Hi all,
I have just installed Narwhal on an msi wind netbook. I can get some websites no problem but others, all favourites such as 'The Great War Forum' simply will not connect. Any solutions out there?

                Jock1

---

### Post by arvevans on 2011-05-06
Loading the "backports" to get wireless running on Natty is fine if you have a wired connection available.  I installed Natty from CD in a location with no wired connection.  Cannot get to the Internet to load the backports, so am broken for now.

---

### Post by pointfive on 2011-05-07
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

This worked for me, thanks!

Every time I upgrade Ubuntu, the wireless stops working. Hope they get it working out of the gate eventually...

---

### Post by Chisikwa on 2011-05-11
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

This worked for me aswell. Thanks!

---

### Post by mikieboy on 2011-05-14
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

just want to thank you for the info. worked perfectly!

---

### Post by phydeaux98038 on 2011-06-01
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

Hate to be the nay-sayer, but I'm in the same boat as Steve.  Cannot see wireless networks, even after following the above steps.  Everything worked prior to 11.04, and nothing since.

```
ewerner@laptop:~$ sudo lspci | grep -i network
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

ewerner@laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:b6000000-b6003fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:db:25:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

ewerner@laptop:~$ modprobe -l | grep b4
kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/cxgb4/cxgb4.ko
kernel/drivers/net/cxgb4vf/cxgb4vf.ko
kernel/drivers/net/b44.ko
kernel/drivers/infiniband/hw/cxgb4/iw_cxgb4.ko

```

Near as I can tell, everything is in place as it should be, but I'm just not getting anywhere.  I'm all ears for any additional suggestions.

---

### Post by JGSD on 2011-06-06
Hi everyone,

I have this exact problem, albeit with the "Atheros Communications Inc. AR9285" that the original poster reported.

> **gseward said:**
> Running Natty 11.04 my usb wireless adapter connects, then fades out.  I have tried to follow the link to "linux-backports-modules-wireless-maverick-generic"  but I am told I am not running Ubuntu!

Surely that package is just for Maverick (10.10) and not Natty (11.04) so it's not surprising that you wouldn't find it. I don't understand how anyone in this thread could have reported the maverick backports to be working on Natty.. especially since the posts were made before Natty was released..  anyway...


> **gseward said:**
> If I try Synaptic and search for "linux-backports-modules-wireless-maverick-generic" or any part thereof I find no wireless backports. 

All I have been able to find in Natty is linux-backports-modules-net-natty-generic but it doesn't seem to solve the problem. I've also tried installing compat-wireless from source but no job.

There is a bug on launchpad at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154?comments=all) which pretty accurately described this issue, though.

---

### Post by buntung on 2011-06-07
Need help please.
Im new using ubuntu 11.04 & I have the same problem with wifi connection :(

mokodongan@satelite:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

Thanks

---

### Post by canek1 on 2011-06-07
Sigh. Me too, on an Atheros AR9287. Does anyone know if this is being worked on?

---

### Post by JGSD on 2011-06-07
> **canek1 said:**
> Sigh. Me too, on an Atheros AR9287. Does anyone know if this is being worked on?

It's been logged as a "Confirmed" bug on Launchpad so I guess that the people who are capable of fixing it at least know that it's a problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154?comments=all)

I hate to say it, but this is exactly the sort of thing that scares people away from Ubuntu, and Linux in general. Someone complained that their old Toshiba Netbook was running slow under XP and that the fonts we all jagged and screen redrawn slow. I suggested Ubuntu as an alternative and, after a lot of convincing and one installation later, I now look like an idiot :-(

Apart from the WiFi problem, performance was actually noticeably better on the netbook with Ubuntu than it was under XP.

I know it's free, I know most people aren't getting paid for making it, but it's just just frustrating to have just a great OS that always seems to be 0.1% short of 'just working' and attracting the masses to using it.

</rant> :-)

---

### Post by ezekielnin on 2011-06-10
thks! It worked for me on ubuntu 11.04 on my dell 1501 laptop!

---

### Post by xq2003 on 2011-06-10
I have a TP-LINK USB WiFi Stick (Atheros Chip) which worked fine until I installed 11.04. Whenever I tried to download a large file, the transfer would start fine (with high speed, I've got 16k ADSL). But then, the download speed would sink to some 32 kB/s while a ping to google.com took between 2000-3000 ms.

Using the 'lsmod' command, I discovered that two different modules (i.e. drivers) were competing for a single resource. It seems that a recent Linux kernel update included the "carl9170" driver which is intended to be an alternative to the "ar9170usb" driver. You can easily find out which driver you are currently using by left-clicking the network-manager's wireless symbol (usually in the top right corner) and selecting "Connection Information" (at the bottom of the list). I solved my problem by blacklisting the Atheros driver:

```

sudo nano /etc/modprobe.d/blacklist.conf

```I just added two new lines at the bottom:

```

blacklist arusb_lnx
blacklist ar9170usb

```After a restart, my WiFi worked again without problems (note: you might need to modprobe carl9170)

---

### Post by ahmadthemoon on 2011-06-11
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by headlessspider on 2011-06-11
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

this "sort of" worked. after reboot the laptop (hp compaq nx6320) did not automatically start scanning for wireless networks. i had to issue the following command in the console to start the process:

```
sudo modprobe b43
```

and i have been using the console to start the wireless everytime i start the computer. :(

---

### Post by amautotech on 2011-06-11
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
  
Can anyone please guide me with further steps...

---

### Post by JoliJef on 2011-06-12
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.
EXCELLENT!  This solved my issue on a Gateway MA3 laptop, which I just installed Ubuntu 11.04 on.  The wireless was the only issue and thanks to your information here, it is now SUCCESSFULLY WORKING!

Thanks a million!
JoliJef

---

### Post by captainapoorv on 2011-06-13
i was unable to uninstall.....the error was........

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory


plz plz plz help me guys m new to ubuntu!!

---

### Post by yannaungko on 2011-06-15
I'm new to ubuntu linux.....I made dual-boot  with window vista by using "Wubi" in my laptop(ACER) .....I want to made internet connection but I have a little difficulties to use wired-connection in our country..... so I choose wireless connection.....but there is a problem of "firmware missing".... The word "Wireless Network" is fade and cannot be used....But Wireless network properly works in Vista...What can I do for this problem? and it seriously important for me...the type of built-in network adapter is Broadcom:BCM94311MCG....

---

### Post by otagurjn on 2011-06-15
hi all
i've been trying to follow the thread, but it seems my problem is a bit different.

i have an HP Pavillion dv6000 dual booted with Ubuntu 11.04. my wireless used to work fine then one day after restarting my computer, both my Windows and Ubuntu partitions failed to recognize (or even detect the presence of) my wireless card. there's nothing to start or install, since it can't even see the driver there.

i've tried the lspci command, none of the lines it returns say any anything about Network Controller or anything that seems like it's related to the wireless card. i've also tried checking commands such as "sudo modprobe wl", "sudo modprobe -r b43 ssb wl", "lspci -vvnn", "rfkill list all", "iwconfig", "sudo rfkill unblock all", "sudo lshw -c network", among others (i found all these commands as part of solutions to other people's problems with ubuntu and wireless cards). the main issue is they just had to try to install/reinstall/force start their card, my computer can't even detect a card.

does anyone know why this may be, how to force my computer to detect the card, or if this is even fixable? any help would be awesome

---

### Post by lemhop on 2011-06-17
HIHO.

Thank you all, I was having the same problems in 11.04 on my Samsung RV511 (Broadcom Corporation BCM4313), but it is now fixed thanks to this thread and [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/).

Had a small hiccup in that I couldn't remove bcmwl-kernel-source via Synaptic initially.  A confused footering about with Synaptic (complete removal) and:

```

sudo rm /var/lib/dpkg/info/bcmwl-kernel-source.{postinst,prerm,postrm}
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get clean

```

from [http://ubuntuforums.org/showthread.php?t=1427221&page=2](http://ubuntuforums.org/showthread.php?t=1427221&page=2), helped get rid of it.

Also, note that you shouldn't be removing or cleaning via apt-get and removing via Synaptic at the same time ([http://ubuntuforums.org/showthread.php?t=954061](http://ubuntuforums.org/showthread.php?t=954061))

:oops:

---

### Post by edmccann on 2011-06-17
This solution worked for me as well.  I'm on a Dell Vostro 1500.

---

### Post by captainapoorv on 2011-06-21
MILLIONS OF THANKS lemhop!!!!!!!! <3 saved me!!! it worked!!! thanks a lot!!!!

---

### Post by andersoncruz on 2011-07-03
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.


Thanks, i,m brazilian and my problem is solved with this.

---

### Post by Ernis1100 on 2011-08-01
The most universal solution would be downloading an extra driver library through the update manager:
Open Ubuntu Software Centre, Go to Edit/Software Sources - then locate "Updates" section.
There you will see a check list.
Check the third line:
 "Proposed Updates (natty-proposed)"
 then run the update manager and update your system.
There should be roughly 140mb of new updates amongst which there will be new driver libraries for various peripherals including usb wireless devices.

---

### Post by andjarnic on 2011-08-04
Thanks for that post.. I am updating 144MB of stuff. I am hoping it resolves my wifi issue. I too had wifi working fine under 10.10 and with 11.04, it finds/uses my MediaLink USB adapter (shows as RAlink rt2800/3070), but like many my network starts normal and a couple seconds into it slows down to a crawl. Because of this, it looks like a good 3 to 4 hour update process for a mere 140MB. If not longer. I will edit this when all is done and hopefully it fixes my wifi issue.

Like many, I am kind of annoyed that every time an update comes out things that were broken, then fixed, get broken again. How does this happen release after release, year after year? It's as if the Ubuntu team keeps a list of all the things that broke, and leave them out again or don't attempt to update those fixes for the new release.

Fingers crossed.

[update] OK..it worked! Ernis has the right info.. it takes a few hours with slow network, but after reboot, my network is full speed again! Good info Ernis!

---

### Post by warda25 on 2011-08-10
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


can any1 plz help me?

---

### Post by jritchie on 2011-09-04
Hi guys I have been having similar problems with wifi. After a lot of searching and trial and error it seems to be working after a fashion now but results are variable . I have copied the results below of the terminal output. 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
jim@jim-PC-RD3D:~$ 

I am not very literate in these matters . My Ubuntu 11.04 is installed alongside windows xp. I had thought to install 10.10 instead since I was very happy with that but I am not sure of the required steps . Installation disc gives me the option of installing alongside but not over the top of 11.04.
Hoping you can help

---

### Post by nisarg127 on 2011-09-18
Wireless Card:- Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

I am facing similar problem as some others are having\
Wireless Networks are detected and displayed but when  i click on any and enter the password it tries to connect and then  show that there is a problem with the password.  
Even my own Networks i.e "Create New Wireless Networks" shows password error.


What i have already tried:-
1) Removed "bcmwl-kernel-source" by using Synaptic Package Manager.And then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. 
- Installation of "firmware-b43-installer" exited with Error.
2) Installed bcmwl-kernel-source from 10.10, as the 11.04 version is broke
- Still same problem


Output of lspci:-
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Any Help??

---

### Post by Herman Munster on 2011-09-18
I also had wireless connectivity problems when I tried just using Natty.  [http://ubuntuforums.org/showthread.php?t=1831186](http://ubuntuforums.org/showthread.php?t=1831186)

I ended up upgrading 10.04LTS to 10.10 to see if the wireless would still work, which it did.  Then I upgraded 10.10 to 11.04 to see if that would work, which thankfully it did.

Hopefully, this ongoing problem will be fixed on the LTS release without having to jump through multiple hoops.

---

### Post by bkratz on 2011-09-18
> **nisarg127 said:**
> Wireless Card:- Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

I am facing similar problem as some others are having\
Wireless Networks are detected and displayed but when  i click on any and enter the password it tries to connect and then  show that there is a problem with the password.  
Even my own Networks i.e "Create New Wireless Networks" shows password error.


What i have already tried:-
1) Removed "bcmwl-kernel-source" by using Synaptic Package Manager.And then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. 
- Installation of "firmware-b43-installer" exited with Error.
2) Installed bcmwl-kernel-source from 10.10, as the 11.04 version is broke
- Still same problem


Output of lspci:-
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Any Help??


B43 is not the right driver for your card. Either the brcm80211 (which is included in the kernel) or the STA driver can be used. You might want to look through this thread and see if it helps.

[http://ubuntuforums.org/showthread.php?t=1783272](http://ubuntuforums.org/showthread.php?t=1783272)

Oh, and I am sure that you will have to remove the b43 drivers. You can use synaptic for that.

---

### Post by nisarg127 on 2011-09-19
> **bkratz said:**
> B43 is not the right driver for your card. Either the brcm80211 (which is included in the kernel) or the STA driver can be used. You might want to look through this thread and see if it helps.

[http://ubuntuforums.org/showthread.php?t=1783272](http://ubuntuforums.org/showthread.php?t=1783272)

Oh, and I am sure that you will have to remove the b43 drivers. You can use synaptic for that.


The other thread helped, Thanks a lot....

---

### Post by bkratz on 2011-09-19
> **nisarg127 said:**
> The other thread helped, Thanks a lot....


Glad it helped you!  Enjoy!

---

### Post by khurtsiya on 2011-09-29
Can anybody help with same problem on Lenovo E520?

---

### Post by skizzikskizziks on 2011-11-09
Hi, I'm looking for some help.

I'm running Ubuntu 11.04, dualbooting Windows 7 and have had intermittent wireless problems. Occasionally I boot up, and my wireless card doesn't work at all. It doesn't show a list of available networks even when I'm in a zone where there definitely are networks. Sometimes this happens, and sometimes it doesn't. Rebooting usually works (i.e. the wireless card works after I reboot) But this time it didn't. I've rebooted in Windows 7 as well as shutting down and restarting without rebooting in Windows 7. 

The last major process I performed in Ubuntu were sudo apt-get update, and sudo apt-get upgrade. The present wireless failure occurred the next time I booted up in Natty Narwhal after updating/upgrading. 

I ran @Terminal: "sudo lspci -v" and got these results:

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Dell Device 0010
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number [omitted]
	Capabilities: [16c] Power Budgeting <?>
	Kernel modules: brcm80211

I also attempted to engage the built-in driver by going to "system settings" -> "additional drivers", but it would not activate the driver. It told me to check the log for details, but for some reason I couldn't access the log (which I don't know anything about). NB I have the administrative account. I also don't know that much about Ubuntu, so I may be making elementary mistakes. 

I'd really appreciate any help solving this problem, as I need my wireless card/drivers to be reliable for my at-home and on-the-go work of various kinds. NB: I tend to access public wireless in various places, in case the networks I'm on matter somehow. 

Thanks!

---

### Post by anuvnu387 on 2012-06-04
[This post]("http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/") has all different ways you can fix wifi problems in ubuntu. Option 4 worked for me:

[http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)

---

### Post by jensbodal on 2013-01-05
> **tacasi said:**
> Steve, I have the same wireless network card; i.e. "Broadcom Corporation BCM4311", and the same problem (no wireless connection, even I cannot see the list of wireless networks) after the 11.04 upgrade. My problem is solved after removing "bcmwl-kernel-source" by using Synaptic Package Manager, then installing "firmware-b43-installer" and "b43-fwcutter" again by Synaptic Package Manager. I hope it solves your problem, too.

Thank you, this solved my problem with with the latest lubuntu release (12.04 I think at this time).  I have a Dell Vostro 1400 with a broadcom wifi card.  I did this right after a fresh install and after reboot wireless was working -- thank you!

---

