---
title: "no detection of wireless connections"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by frankie5555 on 2013-04-09
Hi 

I currently enjoy the pleasure of running a dualboot of Ubuntu 12.04 along win7.
As both a google search and the Ubuntu Forum shows, i too am facing issues
regarding my realtek wlan. For starters i should say i installed Ubuntu via a USB key(not sure if it matters.)

lspci -nn | grep 0280 gives me this info:
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

iwconfig gives me this:
eth0      no wireless extensions.

lo        no wireless extensions.

 dmesg | grep -i firm gives me this:
[    0.391757] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    6.010746] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x250f01)
[    6.602018] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS



Fortunately i do have a wired connection available but only for so long. Hope u guys can help.

---

