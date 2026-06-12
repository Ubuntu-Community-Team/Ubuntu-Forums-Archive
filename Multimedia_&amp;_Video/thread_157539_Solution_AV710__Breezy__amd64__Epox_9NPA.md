---
title: "Solution: AV710 / Breezy / amd64 / Epox 9NPA"
date: 2006-04-09
forum: Multimedia &amp; Video
---

### Post by park on 2006-04-09
I recently built a box based on Arstechnica hotrod recommendations from Jan 06.  Details:
EPoX 9NPA mobo
AMD Athlon 64 3700+ 2.2G
2 GB D400 RAM
nVidia GeForce 6600V+
Chaintech AV710 sound card
Hauppauge WinTV

I installed Ubuntu 5.10 for amd64, which went essentially without a hitch.

Summary of my solution:
Move the card to pci slot 1. The primary cause of the problem, as far as I can see, was the slot the card was in.  I have three pci slots on this motherboard, and two PCI cards (a bttv tuner card and AV710).  The configuration that gave me grief was :
[FONT="Courier New"]
CPU   | slot 1  | slot 2 | slot 3 | Note
CPU   | nothing | bttv   | av710  | Intermittent, usually broken.
CPU   | av710   | bttv   | naught | Works.
[/FONT]

Other details of the installation (which may or may not be required):
To file /boot/grub/menu.lst
add "pci=noacpi" to the "kernel" line
To file /etc/modutils/alsa-base
add the lines
options model=av710
options srate=44100
To play sound through xmms, use the alsa plugin but set the device to "plughw:1". It is ":1" because the onboard sound gets card 0.  I frankly don't understand ALSA very well.  Unbelievably complex.  The error I was getting when I hit play (visible by starting XMMS from the command line) was "Sample format not available for playback"

The file changes come from a thread on head-fi.org
[http://www4.head-fi.org/forums/showthread.php?t=123889&highlight=av710+alsa](http://www4.head-fi.org/forums/showthread.php?t=123889&highlight=av710+alsa)

As a note, I am extremely pleased with the sound quality.  It has been a long time since I tried an internal sound card, but getting away from the SoundBlaster line is nice (native 44.1 KHz support is a good thing).  I am not, I should note, a game player.  There are still the occasional clicks due to bus noise, but for $25 and an internal card I think its unavoidable.

Detailed Problem History:

The problem I encountered was that the AV710 would only be intermittently detected, and when it was not detected neither was the Hauppauge card.  

boot switches that changed the behavior, but did not fix anything, are various combinations of 
pci=noacpi
pci=biosirq
pci=routeirq

Everything is currently

Some of the errors (pulled from /var/log/messages) are:
----- set 1 ----
ICE1724: probe of 0000:01:02.0 failed with error -5
ACPI: PCI Interrupt 0000:01:03.0[A]: no GSI
kernel: [ 6072.415272] unable to grab IRQ 255
ACPI: PCI Interrupt 0000:01:03.0[A]: no GSI
kernel: [ 6072.415272] unable to grab IRQ 255
ICE1724: probe of 0000:01:03.0 failed with error -5
kernel: [ 6072.415288] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
kernel: [ 6072.593572] ACPI: PCI interrupt for device 0000:01:04.0 disabled
---- end set 1 ----

----- set 2 ----
ICE1724: probe of 0000:01:07.0 failed with error -5
kernel: [   95.491864] PCI: No IRQ known for interrupt pin A of device 0000:01:08.0. Probably buggy MP table.
kernel: [   95.491871] unable to grab IRQ 0
kernel: [   95.491876] ICE1724: probe of 0000:01:08.0 failed with error -5
kernel: [   95.670027] ICE1724: probe of 0000:01:09.0 failed with error -5
kernel: [   95.670036] PCI: No IRQ known for interrupt pin C of device 0000:01:0a.0. Probably buggy MP table.
kernel: [   95.670042] unable to grab IRQ 0
---- end set 2 ----

Other relevant links
[http://www.ussg.iu.edu/hypermail/linux/kernel/0010.3/0728.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0010.3/0728.html)
[http://www4.head-fi.org/forums/showthread.php?t=75454](http://www4.head-fi.org/forums/showthread.php?t=75454)
[http://www4.head-fi.org/forums/showthread.php?t=123889&highlight=av710+alsa](http://www4.head-fi.org/forums/showthread.php?t=123889&highlight=av710+alsa)[/FONT]

---

