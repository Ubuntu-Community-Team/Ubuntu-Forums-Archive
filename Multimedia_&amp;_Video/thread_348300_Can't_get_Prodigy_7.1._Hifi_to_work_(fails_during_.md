---
title: "Can't get Prodigy 7.1. Hifi to work (fails during boot)"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by Thomas_R on 2007-01-28
Hi there,

I try to get the soundcard Prodigy 7.1 Hifi to work. But it fails during start up. dmesg results in

```

[17179590.696000] ice1724: No matching model found for ID 0x38315441
[17179590.696000] ice1724: Invalid EEPROM (size = 120)
[17179590.696000] ACPI: PCI interrupt for device 0000:07:04.0 disabled
[17179590.696000] ICE1724: probe of 0000:07:04.0 failed with error -5

```

lspci -v shows the following:

```

07:04.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
        Subsystem: Unknown device 3138:4154
        Flags: medium devsel, IRQ 169
        I/O ports at 9a00 [size=32]
        I/O ports at 9900 [size=128]
        Capabilities: <access denied>

```

It looks as if modprobe chooses the right driver (snd-ice1724) but fails to link it to the card.

Anyone with an idea?

Thx, 
Thomas

---

### Post by DuGi on 2007-10-11
i have the same problem with Prodigy HD2 :(

dmesg:

[ 12.820000] ice1724: No matching model found for ID 0x37315441
[ 12.820000] ice1724: Invalid EEPROM (size = 120)
[ 12.820000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
[ 12.820000] ICE1724: probe of 0000:01:08.0 failed with error -5


lspci:

01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
Subsystem: Unknown device 3137:4154
Flags: medium devsel, IRQ 22
I/O ports at bc00 [size=32]
I/O ports at b800 [size=128]
Capabilities: <access denied>

---

### Post by gmhafiz on 2008-04-30
> **DuGi said:**
> i have the same problem with Prodigy HD2 :(

dmesg:

[ 12.820000] ice1724: No matching model found for ID 0x37315441
[ 12.820000] ice1724: Invalid EEPROM (size = 120)
[ 12.820000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
[ 12.820000] ICE1724: probe of 0000:01:08.0 failed with error -5


lspci:

01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
Subsystem: Unknown device 3137:4154
Flags: medium devsel, IRQ 22
I/O ports at bc00 [size=32]
I/O ports at b800 [size=128]
Capabilities: <access denied>

I've got the same problem with Audiotrak HD2 as well. The reason it is not working is simple. Prodigy HD2 is only supported in the ALSA version 1.0.16 Ubuntu 7.10 only has ALSA version 1.0.14. So Prodigy HD2 is not supported under Ubuntu 7.10

To fix this problem, you must upgrade ALSA to version 1.0.16. This brings up a new question.

I did an ALSA upgrade using instruction from [http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html]("http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html")  to version 1.0.16 with no problem. I just include ice1724 modules to the following command:

$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=**ice1724**,hda-intel,intel8x0m,intel8x0,usb-audio --with-oss=yes ; sudo make ; sudo make install

After upgrade:

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Apr 29 2008 for kernel 2.6.22-14-generic (SMP).

However, when I start ALSA, I got this

$ sudo /etc/init.d/alsa-utils restart
[sudo] password for gmhafiz:
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: set_control:1300: incompatible field type for control #1'...                                  amixer: Invalid command!
                                                                         [ OK ]

My Audiotrak Prodigy HD2 still does not work. 

FYI, Audiotrak Prodigy HD2 works out of box by using Fedora 9 beta (on both live cd and after install). It's worth mentioning that Fedora 9 uses ALSA 1.0.16 and kernel 2.6.25. Driver for Prodigy HD2 is included in that latest kernel.

Any idea why my sound card still does not work even after upgrading to ALSA 1.0.16? What did I missed? Since I have a working Audiotrak Prodigy HD2 on Fedora 9 on my second partition. Is there any configuration files that I can salvage from my installation of Fedora 9?

---

