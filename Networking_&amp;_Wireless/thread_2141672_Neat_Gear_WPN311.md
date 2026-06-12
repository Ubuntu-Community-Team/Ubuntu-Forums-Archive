---
title: "Neat Gear WPN311"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by intrepid1960 on 2013-05-03
Can't get Ubuntu to recognize my Neat Gear WPN311 wireless card.  Any suggestions on how to resolve?

Mike

---

### Post by intrepid1960 on 2013-05-03
Ok, so I visited [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) and went through the process to get the driver installed.

Everything worked until I got to:


sudo modprobe ndiswrapperand received the following error: [COLOR=#222222][FONT=Verdana]FATAL: Module ndiswrapper not found.
[/FONT][/COLOR]
...Did this....
ndiswrapper -l  returns the following
wg311v3 : driver installed
device (11AB:1FAA) present


...Additional info.....

lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV516 [Radeon X1300 Pro] (Secondary)
03:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
03:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 61)

Downloaded dkms

.......Then tried this and
sudo dpkg -i ndiswrapper -dkms*.deb

......this was the resut
dpkg: error processing ndiswrapper (--install):
 cannot access archive: No such file or directory
dpkg: error processing -dkms*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper
 -dkms*.deb

Now I am stumped.

What am I missing?

Mike

---

