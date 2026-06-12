---
title: "Netgear WG311 Wireless Help Needed"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by intrepid1960 on 2013-05-06
[COLOR=#000000]Ok, so I visited [/COLOR][https://help.ubuntu.com/community/Wi...tgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")[COLOR=#000000] and went through the process to get the driver installed.[/COLOR]

[COLOR=#000000]Everything worked until I got to:[/COLOR]


[COLOR=#000000]sudo modprobe ndiswrapper

and received the following error: [/COLOR][COLOR=#222222][FONT=Verdana]FATAL: Module ndiswrapper not found.
[/FONT][/COLOR]
[COLOR=#000000]...Did this....[/COLOR]
[COLOR=#000000]ndiswrapper -l returns the following[/COLOR]
[COLOR=#000000]wg311v3 : driver installed[/COLOR]
[COLOR=#000000]device (11AB:1FAA) present[/COLOR]


[COLOR=#000000]...Additional info.....[/COLOR]

[COLOR=#000000]lspci[/COLOR]
[COLOR=#000000]00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)[/COLOR]
[COLOR=#000000]00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)[/COLOR]
[COLOR=#000000]00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)[/COLOR]
[COLOR=#000000]00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)[/COLOR]
[COLOR=#000000]00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)[/COLOR]
[COLOR=#000000]00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)[/COLOR]
[COLOR=#000000]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)[/COLOR]
[COLOR=#000000]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)[/COLOR]
[COLOR=#000000]00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)[/COLOR]
[COLOR=#000000]00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)[/COLOR]
[COLOR=#000000]00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)[/COLOR]
[COLOR=#000000]00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)[/COLOR]
[COLOR=#000000]00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)[/COLOR]
[COLOR=#000000]00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)[/COLOR]
[COLOR=#000000]00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)[/COLOR]
[COLOR=#000000]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)[/COLOR]
[COLOR=#000000]01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV516 [Radeon X1300/X1550 Series][/COLOR]
[COLOR=#000000]01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV516 [Radeon X1300 Pro] (Secondary)[/COLOR]
[COLOR=#000000]03:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/COLOR]
[COLOR=#000000]03:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 61)[/COLOR]

[COLOR=#000000]Downloaded dkms[/COLOR]

[COLOR=#000000].......Then tried this and[/COLOR]
[COLOR=#000000]sudo dpkg -i ndiswrapper -dkms*.deb[/COLOR]

[COLOR=#000000]......this was the resut[/COLOR]
[COLOR=#000000]dpkg: error processing ndiswrapper (--install):[/COLOR]
[COLOR=#000000]cannot access archive: No such file or directory[/COLOR]
[COLOR=#000000]dpkg: error processing -dkms*.deb (--install):[/COLOR]
[COLOR=#000000]cannot access archive: No such file or directory[/COLOR]
[COLOR=#000000]Errors were encountered while processing:[/COLOR]
[COLOR=#000000]ndiswrapper[/COLOR]
[COLOR=#000000]-dkms*.deb[/COLOR]

[COLOR=#000000]Now I am stumped.[/COLOR]

[COLOR=#000000]What am I missing?[/COLOR]

[COLOR=#000000]Mike[/COLOR]

---

