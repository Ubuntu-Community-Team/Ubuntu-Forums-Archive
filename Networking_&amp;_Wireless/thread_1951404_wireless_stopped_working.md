---
title: "wireless stopped working"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by bretmcbret on 2012-04-02
I have a Dell Inspiron E1505 that I installed Lubuntu on in January after headaches with Unity and really appreciated its lightweight speed. Everything worked fine and then last week when I booted my wireless connection stopped working for some reason. I checked the forums for any clues, reinstalled the OS, and still nothing. The connector is an Intel Corporation PRO/Wireless 3945ABG[Golan] Network Connection (rev 02). Note: My internet connection at home entirely wireless, no hardline modem connection, so I’m re-typing everything below from my terminal screen.

Some command output info

cat /etc/lsb-release: uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION=”Ubuntu 11.10”
Linux bretmcbret 3.0.0-12-generic #20-Ubuntu Fri Oct 7 14:50 UTC 2011 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net

03.00.0 Ethernet controller [0200]]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
Subsystem: Dell Inspiron 6400 [1028:01af]
Kernel Driver in use: b44

0b.00.0 Network Controller [0280]: Intel Corporation PRO/Wireless 3954ABG [Golan] Network Connection [8086:4222] (rev 02)
Subsytem: Intel Corporation Device [8086:1020]
Kernel driver in use: iwl3945

iwconfig

lo	no wireless connection
eth0	no wireless connection
wlan0	IEEE 802.11abg ESSID:off/any
	Mode:managed Access Point: Not-Associated Tx-Power=off
	Retry long limit:7 RTS thr:0ff Fragment thr:off
	Power Management:off

rfkill list all

The program ‘rfkill’ is currently not installed. You can install it by typing: sudo apt-get install rfkill


lsmod too long to reproduce. Is there any specific line I should be paying attention to?

nm-tool

State: disconnected

Device: wlan0

Type:		802.11 WiFi
Driver:		iwl3945
State:		unavailable
Default:	No
HW Address:	00:13:02:AA:93:69

Capabilities:

Wireless Properties
WEP Encryption:	 yes
WPA Encryption:	yes
WPA2 Encryption:	yes

Wireless Access Points

Device: eth0

Type:		Wired
Driver:		b44
State:		unavailable
Default:	no
HW Address:	00:15:C5:22:64:5B

Capabilities:
Carrier Detect:		yes
Speed:			10 Mb/s

Wired Properties
Carrier:	off


sudo iwlist scan

lo		Interface doesn’t support scanning
eth0		Interface doesn’t support scanning
wlan0		Interface doesn’t support scanning : Network is down


I checked out this thread:

[http://ubuntuforums.org/showthread.php?t=1928087](http://ubuntuforums.org/showthread.php?t=1928087)



but it didn’t help me. Any suggestions?

---

### Post by chili555 on 2012-04-02
Please run and post:```
dmesg | grep iwl
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

We hope we do not see 'iwl3945: Radio disabled by HW RF Kill switch.' If you do, look for the hardware switch on your laptop and move it back to 'Enable.'

---

### Post by bretmcbret on 2012-04-25
First off, apologies for the WAY tardy reply. After checking to see if it was a hardware problem as chili555 suggested--it wasn't--I ended up getting frustrated and re-installing the OS a third time and everything started working again. So I have no idea what I was doing wrong though everything since has been working fine. I wish had some info/knowledge to impart, but I do not.

B

---

### Post by km3952 on 2012-04-28
> **bretmcbret said:**
> First off, apologies for the WAY tardy reply. After checking to see if it was a hardware problem as chili555 suggested--it wasn't--I ended up getting frustrated and re-installing the OS a third time and everything started working again. So I have no idea what I was doing wrong though everything since has been working fine. I wish had some info/knowledge to impart, but I do not.

B

You might find it happening again if it is a loose connection inside your machine.

---

