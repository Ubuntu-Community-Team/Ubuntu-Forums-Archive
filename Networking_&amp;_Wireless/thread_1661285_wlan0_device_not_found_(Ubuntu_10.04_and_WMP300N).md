---
title: "wlan0 device not found (Ubuntu 10.04 and WMP300N)"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Valvador on 2011-01-06
Hey all,

I understand there are plenty of topics discussing the WMP300N install on Ubuntu, which I have read almost all of.

I installed ndiswrapper along with ndisutilities and ndisgtk. I found the original driver disk. In fact I attempted to use the Windows 7, XP, and Vista versions. My problem is that when my system starts up and after installing the driver, I only get options for the wired networks. Wireless doesn't even let me check it's options.

When I type in "ndiswrapper -l" I get that the driver has been successfully installed, however when I try to get iwconfig to list all devices I have only two devices showing up.

The devices are
eth0
lo

eth0 being the motherboard Ethernet port and lo just being the usual 127.0.0.1 IP address.

wlan0 doesn't exist.

Does anyone know if this is just not reading my card or do I have to input the information manually about the cards existence?

This computer is Dual Booted with Windows 7, and my Wireless Card works perfectly on the Windows 7 side.

Any suggestions?

---

### Post by deuscapturus on 2011-05-04
If it makes you feel better I've also had the same problem with no success.  Research has lead me to believe it's a 64bit problem.  I'm now convinced that ndiswrapper will not work for this card on a 64bit install.  I'm currently working on a getting the native broadcom driver to work; It's worked for me in the past.

Let me know if you have since solved this problem.

---

### Post by akira7799 on 2011-06-09
deuscapturus,
 
Have you had any luck changing the Broadcom driver to work with the WMP300N?
 
I'm running a x64 architecture of 11.04 and the Broadcom driver works until it experiences some light network traffic.  Then everything freezes up.
 
Thanks for the info about the 64 bit problem.  I might move to 32 bit to deal with this issue.
 
Any more info in regards in getting the native Broadcom driver to work with the WMP300N?
 
Thanks, 
Dave

---

### Post by deuscapturus on 2011-06-09
I did get this working on 64bit, but not with native drivers.  I did get ndiswrapper to function using the bcmwl5 Windows drivers.  The problem was that I had had the wl driver loaded and conflicting with ndiswrapper.

I added all of the following to /etc/modprobe.d/blacklist(.conf) to get ndiswrapper working:

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist wl

reboot afterwards.

---

### Post by akira7799 on 2011-06-14
deuscapturus, 

Thanks very much for the insight!  It worked for me on a 64 bit install of 11.04.  I blacklisted 

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist wl

Installed ndiswrapper with the original BCMWL5 driver and it picked it up almost immediately.

Thanks again,
Dave

---

### Post by U-Toto on 2011-09-19
Hi,

I have been reading these posts for days. I have a Dell Optiplex 320 (32 bit) with 10.04.3 running dual booted w/XP. I have the same PCI card and have not been able to get it to function in Ubuntu. Only in XP. 

I have tried so many things, I am actually not even sure of what my settings for it are anymore.:?

It seems help offered has worked for some. Would you please try to assist me with my problem? I imagine it is the same or close to what fixed for the others.

lspci gives me this....

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:01.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
02:09.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

