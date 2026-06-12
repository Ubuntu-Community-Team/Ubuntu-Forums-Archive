---
title: "Ndiswrapper and wireless card configuration"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by mattb0m on 2012-08-27
I believe I have been successful in installing my Windows XP driver under ndiswrapper, however, I cannot seem to bring my wireless interface up.

My laptop is: Dell Latitude D600

OS:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

ndiswrapper -l gives me:
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

lspci output:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:00.0 USB controller: NEC Corporation USB (rev 43)
03:00.1 USB controller: NEC Corporation USB (rev 43)
03:00.2 USB controller: NEC Corporation USB 2.0 (rev 04)

This may or may not be of interest bu, if I ifconfig wlan0 up:
STIOCSIFFLAGS: no such file or directory.

Thank you for any assistance you can offer!

---

### Post by kurt18947 on 2012-08-27
Are you certain you need NDISwrapper with this Broadcom chipset?  I don't have any Broadcom devices so am not knowledgeable about Broadcom issues.  There are some newer WiFi chipsets that don't have native Linux support so require NDISwrapper.  This Broadcom chip has been around a while.  Did you happen to check 'additional drivers' while plugged into a wired connection?  Here is a thread where a Broadcom 4306 chipset was successfully enabled:

[http://ubuntuforums.org/showthread.php?t=2024714&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=2024714&highlight=broadcom+4306)
Post #2 of that thread looks useful.

I suspect that if you want to pursue this, you'll want to uninstall NDISwrapper first.  It seems native driver solutions are preferred over wrappers where native drivers are available.

---

### Post by mattb0m on 2012-08-27
Excellent. I will try this and report back.

---

### Post by mattb0m on 2012-08-27
Thank you for pointing me in the right direction.
I should have properly consulted the forums and the list of supported b43 chipsets.
This fixed my problem.

---

### Post by kurt18947 on 2012-08-27
> **mattb0m said:**
> Thank you for pointing me in the right direction.
I should have properly consulted the forums and the list of supported b43 chipsets.
This fixed my problem.

I'm glad it worked for you.  One of the secrets to linux hardware happiness is to not buy just-released-today or really uncommon stuff.  Your chipset has been around for a while and is fairly popular thus well supported.

---

