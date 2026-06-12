---
title: "Wireless in Acer Aspire One is unreliable with any driver"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by MihaiM on 2009-02-08
Hello,

I am having a hard time using the wireless connection on my Acer Aspire One. The issue I have is that with any driver I use (either mad-wifi or ndiswraper) I am not able to connect from the first attempt. It hangs at connection and I get a timeout in about 30-60 seconds without any error. Same issue with any driver. Wireless network list displays fine, just cannot connect reliably. Router is a Linksys WRT54GL with DD-WRT that works beautifully for a couple of laptops and wifi-enabled phones.

lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
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
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

Some lines with the error from syslog:
> Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  Activation (wlan0) failed for access point (dd-wrt-linksys) 
Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  Marking connection 'Auto dd-wrt-linksys' invalid. 
Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  Activation (wlan0) failed. 
Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Feb  8 21:40:15 acer-aspire-one NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) starting connection 'Auto dd-wrt-linksys' 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto dd-wrt-linksys' has s
ecurity, but secrets are required. 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Feb  8 21:40:20 acer-aspire-one NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto dd-wrt-linksys' has sec
urity, and secrets exist.  No new secrets needed. 

I was able to find this bug on other places on the Internet, but without a solution.

Regards.

---

### Post by jimv on 2009-02-08
Does the same thing happen if you use WICD instead of Network-Manager?

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by MihaiM on 2009-02-08
Just checked and Wicd does not make the connection work in a reliable way.

Also I have activated syslon on dd-wrt and there are no timeouts or errors there.

---

### Post by jsmasterx on 2009-02-08
I have the same problem with my aspire one. With windows xp it'S working fine.

I can connect to my network but I get cut off if I break the 800kbits download...

---

### Post by danni-la on 2009-02-08
try the backports drivers

sudo aptitude install linux-backports-modules-intrepid-generic

this is the only thing that works consistently on my one.

Cheers Danni

---

### Post by MihaiM on 2009-02-09
Hello,

Thanks for both your responses. The solution might be using ath5k from the backport modules. It is the only one that connects every time and I am testing right now downloading via torrent and I get consistent over 1MB (the usual for my Internet line).

I will mark this as solved as soon as I do more testing, but so far it looks promising. 

Regards,
Mihai.

Later Edit: Looks solved now. Everything works at full speed and seams to connect every time. Thanks for your support.

---

