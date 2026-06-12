---
title: "Intel 4965 AGN"
date: 2010-10-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MilkeySUFC on 2010-10-09
Hi,

I installed the RC to a 2nd partition on my Samsung Q45 laptop and everything was going fine. Set up everything and connected to my 802.11n WAN, WPA2 password and made sure Auto Connect was ticked in "Connection Properties".

Did upgrade after setting up and it required a reboot but now it will not connect to my 802.11n WAN anymore.

It seems to see it and goes through the process of connecting but takes 3 to 4 minutes and then asks for the password again.

I've had to resort to connecting to the 802.11g WAN.

Has anyone got any ideas?

Milkey

```

mike@MZJ-Q45:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
04:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
04:09.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
04:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
04:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)



```

---

### Post by Quackers on 2010-10-09
Mine's been fine through all upgrades and updates but somebody else had a similar problem to you. I'm not sure whether it was solved or not though, I'm afraid. Have you used the search feature using Intel 4965 or similar?

---

### Post by MilkeySUFC on 2010-10-09
Hi Quackers,

Thanks for your response.

I tried searching and the only thing that came up for "Intel 4965" in search was about ndiswrapper.

Thanks,
Milkey

---

### Post by forcecore on 2010-10-09
I had conflicts with bluetooth when i switched bt off then wifi connecting was slow or did not connect but when bt works then it is fine. I had two choices 1: keep bt on 2: disconnect bt module physically.

---

