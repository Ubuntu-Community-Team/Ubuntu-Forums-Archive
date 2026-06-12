---
title: "Hauppage wintv PVR  150 &quot;Invalid eeprom&quot;"
date: 2009-04-25
forum: Mythbuntu
---

### Post by Maki_doda on 2009-04-25
I have an hauppage wintv pvr 150 card, and when i can view the tv stream with mplayer, but it shows only static, when i search for channels with mythtv it doesn't find anything.

Dmesg shows:

ivtv0: Autodetected Hauppauge card (cx23416 based)
ivtv 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
tveeprom 1-0050: Encountered bad packet header [ff]. Corrupt or not a Hauppauge eeprom.
ivtv0: Invalid EEPROM

after scanning with mythtv i get tunner type not set errors in dmesg.
This card worked for me in archlinux about a day before breaking after a restart, i have tried in windows but i didn't get as far as on linux with showing the static.

---

### Post by Maki_doda on 2009-04-27
Seems i have solved it with adding options ivtv tuner=56,56 to modprobe.conf

---

