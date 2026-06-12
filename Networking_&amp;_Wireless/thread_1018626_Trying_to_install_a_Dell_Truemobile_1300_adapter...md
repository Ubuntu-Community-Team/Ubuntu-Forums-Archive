---
title: "Trying to install a Dell Truemobile 1300 adapter..."
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Terpsichore on 2008-12-22
[LIST=1]
[/LIST]For starters, thanks for reading this :).

I am a complete and utter linux newbie, but I installed Ubuntu 8.10 yesterday, and after a few little teething problems I got it working ok. 

I looked up a few things and noticed a lot of people have had similar problems, but trying to read and execute the instructions when I have to switch from Ubuntu back to Windows every time I want to check something is getting a bit wearing and I'm not making much progress.

Would it be possible for someone to talk me through exactly how to go about:
[LIST=1]
[*]Installing ndiswrapper
[*]Setting up my drivers
[/LIST]

Thanks for your patience and any help you can give me.

---

### Post by ieee488 on 2008-12-22
You shouldn't need ndiswrapper in Ubuntu 8.10 for this wireless adapter if it is the one with the Broadcom 3406 chipset.

Someone with Compaq and a wifi card with Broadcom 3406 chipset had his wifi card working out of the box.

---

### Post by Terpsichore on 2008-12-22
That's strange: I connected it to my computer and ran everything I could find (including setting up wireless networks) but the adapter's indicators don't light up.
I'm trying to use it with a BT broadband 1800 home hub, if that makes any difference...

---

### Post by Ayuthia on 2008-12-22
Can you post the results of lspci -nn from the Terminal?  It will help us see which chipset you have and help us point you in the right direction.

---

### Post by Terpsichore on 2008-12-23
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:05.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)
01:09.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)

The results of lspci -nn.

---

### Post by ieee488 on 2008-12-23
I don't see anything for wireless in that listing.


Mine listing has 
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

---

