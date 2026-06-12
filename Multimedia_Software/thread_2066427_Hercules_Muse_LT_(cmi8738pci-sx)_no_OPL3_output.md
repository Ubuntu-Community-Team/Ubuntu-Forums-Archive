---
title: "Hercules Muse LT (cmi8738/pci-sx) no OPL3 output"
date: 2012-10-04
forum: Multimedia Software
---

### Post by odierick on 2012-10-04
Hi,

I just bought a Hercules GameSurround Muse LT sound card today to replace a fried Trust SC-5100.
I replaced the Trust pci card with the Hercules one.
I can get sound from the card but not from OPL3 MIDI.

The software is configured like this:
Ubuntu 10.04

fm_port=0x388 added to the options line in /etc/modprobe.d/alsa-base.conf
-> no 'no OPL device at 0x388' error or any opl or cmipci relevant error in dmesg or kern.log

sbiload is called to load the fm chip with opl3 samples.
-> no error from sbiload.

synth is unmuted and 100% volume in alsamixer.
OPL3 FM is listed by aconnect -o as client 21:0
OPL3 FM is listed by aplay -l as client 21:0
OPL3 FM is listed by aplaymidi -l as client 21:0
(client 20:0 is mpu401 port)

aplaymidi -p 21:0 file.mid appears to play file, but no sound is heard.

Before buying the Hercules card I was woried that it didn't have the OPL3 support that the Trust SC-5100 had. I checked everywhere and couldn't find any specs for that card.

The Trust card was build arround a CMI8738/pci-6ch-lx chipset.
The Hercules card is build arround a CMI8738/pci-sx chipset.
The chipset specs from C-Media states that all three models (SX, MX and LX) have FM OPL3 capability.

If it actually has, I'll dig further into why I can't get the OPL3 to emit sound. If not, I'll use timidity, but I would rather avoid that.

Can someone please confirm that Hercules GameSurround Muse LT has OPL3 support or not?

Olivier

---

