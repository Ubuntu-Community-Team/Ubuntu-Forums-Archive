---
title: "Q: Which gfx card for audio over HDMI"
date: 2010-02-05
forum: Mythbuntu
---

### Post by GuiGuy on 2010-02-05
I'm going to the local computer fair in the morning to pick up a graphics cards that will let me do audio over HDMI from an ASUS M3A mobo  an ASUS M2H mobo/ Both have spdif headers on the main board. 

This [nvidia 9500 based card]("http://www.ddcomputer.com.au/prod-EN9500GT-DI-1G-proddes_ASUS_EN9500GT-DI-1G.html") seems to be good enough. All the more so if there's a passively cooled version.

Comments? Suggestions?

TIA

---

### Post by ian dobson on 2010-02-05
Hi,

I have a 9600gt in my MythFrontend and audio over HDMI works really well, going from the SPDIF port on the motherboard to the SPDIF passthough on the card:

```

nvclock -i
-- General info --
Card:           nVidia Geforce 9600GT
Architecture:   G94 A1
PCI id:         0x622
GPU clock:      702.000 MHz
Bustype:        PCI-Express

-- Shader info --
Clock: 1728.000 MHz
Stream units: 64 (1111b)
ROP units: 16 (1111b)
-- Memory info --
Amount:         512 MB
Type:           256 bit DDR3
Clock:          899.996 MHz

-- PCI-Express info --
Current Rate:   16X
Maximum rate:   16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 66C

-- VideoBios information --
Version: 62.94.3c.00.00
Signon message: GV-N96TSL-512I/F11
Performance level 0: gpu 650MHz/shader 1625MHz/memory 900MHz/1.10V/100%
VID mask: 3
Voltage level 0: 1.00V, VID: 0
Voltage level 1: 1.05V, VID: 1
Voltage level 2: 1.10V, VID: 2

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L
default:CARD=Intel
    HDA Intel, ALC888 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

Just make sure you get the SPDIF passthrough cable with the card. It's not always included with the graphic card.

Regards
Ian Dobson

---

### Post by GuiGuy on 2010-02-05
> **ian dobson said:**
> Hi,

I have a 9600gt in my MythFrontend and audio over HDMI works really well, going from the SPDIF port on the motherboard to the SPDIF passthough on the card:
Just make sure you get the SPDIF passthrough cable with the card. It's not always included with the graphic card.



Thanks, Ian. The ASUS card has the cable included. 

Cheers,

---

