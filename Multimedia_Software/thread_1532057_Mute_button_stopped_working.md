---
title: "Mute button stopped working"
date: 2010-07-15
forum: Multimedia Software
---

### Post by svaucher on 2010-07-15
In the last week, I noticed that my compaq 6710b physical controls for volume control/mute stopped working correctly. The volume control is not working anymore and the mute "unmutes" itself after precisely 1 minute.

I was wondering:
1/ did an update modify anything
2/ is there a way for me to know if the problem is physical? like a physical signal sniffer of some sort, or a log that indicates that I pressed mute
3/ Am I alone? and if not, does anyone know of a workaround?

Am running 10.4
Linux vaucher-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

thanks,
Stephane

---

### Post by lidex on 2010-07-18
Is there a specific thing going on when it unmutes itself, such as skype? 
Post this terminal output for me please:
```
sudo dmidecode -t bios
```

---

### Post by svaucher on 2010-07-22
Hmmm, after a reboot, it started working again... Skype was not running at the time.  In any case, here is the result of the command (after reboot).

$dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: 68DDU Ver. F.14
	Release Date: 11/04/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 15.20
	Firmware Revision: 113.46

And thank you for the response.
Stephane

---

