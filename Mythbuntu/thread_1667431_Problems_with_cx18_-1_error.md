---
title: "Problems with cx18 -1 error"
date: 2011-01-14
forum: Mythbuntu
---

### Post by powellmd on 2011-01-14
i have been searching through the forums for days with no solution to my problem. i cant add my hauppauge hvr-1600 tuner to capture devices after mythbuntu 10.10 install

dmesg | grep cx18 reads as follows

```
[   21.414186] cx18:  Start initialization, version 1.4.0
[   21.414297] cx18-0: Initializing card 0
[   21.414304] cx18-0: Autodetected Hauppauge card
[   21.454476] cx18 0000:02:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.646548] cx18-0: cx23418 revision 01010000 (B)
[   22.329200] cx18-0: Autodetected Hauppauge HVR-1600
[   22.329205] cx18-0: Simultaneous Digital and Analog TV capture supported
[   23.028220] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   23.040325] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   23.040337] DVB: registering new adapter (cx18)
[   23.097586] cx18-0: frontend initialization failed
[   23.098832] cx18-0: DVB failed to register
[   23.099407] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   23.099850] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   23.101127] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   23.103365] cx18-0: Error -1 registering devices
[   23.188198] cx18-0: Error -1 on initialization
[   23.188294] cx18: probe of 0000:02:09.0 failed with error -1
[   23.190060] cx18:  End initialization
```lspci -v reads

```
02:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
    Subsystem: Hauppauge computer works Inc. Device 740c
    Flags: bus master, medium devsel, latency 66, IRQ 18
    Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel modules: cx18

```If anyone could help me get this mythbuntu box operational i would be very appreciative

thx

---

### Post by thatguruguy on 2011-01-14
1. What exact problems are you having? Are ***no*** tuners showing up at all, or is it just that your particular tuner isn't listed?

2. What options are being shown under tuners?  It's possible that your card is listed, but not in the way you expect.  For instance, I have a Hauppauge 950Q, which is a hybrid analog/digital tuner usb stick.  The digital side shows as follows:  
Card type: DVB DTV capture card(v3.x)
DVB device number: /dev/dvb/adapter0/frontend0
Frontend ID: Auvitek AU8522 QAM

---

### Post by powellmd on 2011-01-14
> **Re: Problems with cx18 -1 error**             
                                                                1. What exact problems are you having? Are ***no*** tuners showing up at all, or is it just that your particular tuner isn't listed?

2. What options are being shown under tuners?  It's possible that your  card is listed, but not in the way you expect.  For instance, I have a  Hauppauge 950Q, which is a hybrid analog/digital tuner usb stick.  The  digital side shows as follows:  
Card type: DVB DTV capture card(v3.x)
DVB device number: /dev/dvb/adapter0/frontend0
Frontend ID: Auvitek AU8522 QAM
No tuners are showing up at all. In fact no tuners show up in any type of category of tuners. and /dev has no video0 or anything like that in it. i have tried compiling new drivers and installing updated firmware to /etc/firmware as directed by [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) with no luck as well.

---

### Post by klc5555 on 2011-01-15
> **powellmd said:**
> No tuners are showing up at all. In fact no tuners show up in any type of category of tuners. and /dev has no video0 or anything like that in it. i have tried compiling new drivers and installing updated firmware to /etc/firmware as directed by [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600) with no luck as well.

It's unusual that the DVB half of a Hauppauge 1600 will fail to be detected by the driver and produce an Error -1. Usually that seems to happen with other, more obscure cards using the same chipset that are only now having support written into the cx18 driver.

One possibility may be, with some motherboards, that the 1600 seems a bit finicky regarding which PCI slot it gets. The first 1600 I got a couple of years ago I installed on a BTX board with 4 PCI slots. It would work properly only in the first slot (closest to the graphics adapter); in the 3rd or 4th slot it would stop the machine from booting altogether.

Have you tried moving the card to a different slot?

---

### Post by powellmd on 2011-01-17
> Have you tried moving the card to a different slot?
I have. In fact i have moved the card to another system altogether and am getting the same error. the first system was an older compaq p4 1.8 ghz on a mb with the pci on a daughterboard. the second system is a relatively new intel mb with a core 2 duo 2.4 ghz. i also tried every pci slot on both boards with the same outcome.

---

### Post by klc5555 on 2011-01-18
> **powellmd said:**
> I have. In fact i have moved the card to another system altogether and am getting the same error. the first system was an older compaq p4 1.8 ghz on a mb with the pci on a daughterboard. the second system is a relatively new intel mb with a core 2 duo 2.4 ghz. i also tried every pci slot on both boards with the same outcome.

Ah, well, that's unfortunate. Hauppauge's FAQ page for the 1600 doesn't mention Linux drivers, of course, but does mention that if the card can't be brought to life (with its Windows driver) in multiple PCI slots, then you should contact their customer support about a possible replacement. 

It may well be, if the DVB tuner on your card can't be initialized in multiple PCI slots on two machines with (at least) two different iterations of the cx18 driver, that the card itself is defective. The cx18 driver (and the related Hauppauge firmware)is a bit quirky with detecting the tveeprom on the the analog side of the most recent versions of this card, but does not normally have any basic detection/initialization difficulties with the DVB side. And you have eliminated the PC hardware itself as the culprit.

---

