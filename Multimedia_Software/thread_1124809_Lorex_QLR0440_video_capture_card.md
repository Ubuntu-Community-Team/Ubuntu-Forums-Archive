---
title: "Lorex QLR0440 video capture card"
date: 2009-04-13
forum: Multimedia Software
---

### Post by nate.a.miller on 2009-04-13
I recently purchased a Lorex QLR0440 4 Port PCI Card and haven't had any luck getting it to work with Intrepid.

Anyone had any experience with this card?

Currently all that I can get from it with both xawtv and tvtime is a blue screen.  The one thing I see that's kind of odd is that there doesn't seem to be a subsystem id associated with this device.  Help please?  Thanks

[EDIT]: I decided to poke around at the device a bit more and it appears that there's an Atmel AT89C2051 micro on there as well (an 8051 architecture) - does that mean I'm going to need to find some firmware somewhere?

Various info below:

**lspci output**:

[INDENT]01:04.0 Multimedia video controller [0400]: Brooktree Corporation Bt878
Video Capture [109e:036e] (rev 11)
       Flags: bus master, medium devsel, latency 32, IRQ 16
       Memory at e1000000 (32-bit, prefetchable) [size=4K]
       Capabilities: [44] Vital Product Data <?>
       Capabilities: [4c] Power Management version 2
       Kernel driver in use: bttv
       Kernel modules: bttv

01:04.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio
Capture [109e:0878] (rev 11)
       Flags: bus master, medium devsel, latency 32, IRQ 3
       Memory at e1001000 (32-bit, prefetchable) [size=4K]
       Capabilities: [44] Vital Product Data <?>
       Capabilities: [4c] Power Management version 2[/INDENT]

**dmesg output**:
[INDENT][   23.500950] bttv: driver version 0.9.17 loaded
[   23.500956] bttv: using 8 buffers with 2080k (520 pages) each for
capture
[   23.502133] bttv: Bt8xx card found (0).
[   23.502156] bttv 0000:01:04.0: PCI INT A -> GSI 16 (level, low) ->
IRQ 16
[   23.502171] bttv0: Bt878 (rev 17) at 0000:01:04.0, irq: 16, latency:
32, mmio: 0xe1000000
[   23.502189] bttv0: using:  *** UNKNOWN/GENERIC ***
[card=0,autodetected]
[   23.502227] bttv0: gpio: en=00000000, out=00000000 in=00f7feff [init]
[   23.533668] bttv0: tuner type unset
[   23.533674] bttv0: i2c: checking for MSP34xx @ 0x80... <6>cx88/2:
cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   23.807060] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   23.807672] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   23.812786] bttv0: registered device video0
[   23.812898] bttv0: registered device vbi0
[/INDENT]

**Info from the INF file for the Windows driver**:
[INDENT]%VEN_109E&DEV_036E%=WJ430V,PCI\VEN_109E&DEV_036E&SUBSYS_6B686A61
%VEN_109E&DEV_0878%=WJ430A,PCI\VEN_109E&DEV_0878&SUBSYS_6B686A61[/INDENT]

---

### Post by nate.a.miller on 2009-04-20
Alright.  I think I got it - wrote a script to try loading the bttv module with each card of the 159 or so currently supported.  Found out that card number 131 basically works.  You just don't get the extra 12 channels.  I'll post more info later when I'm back at my Ubuntu box.

---

### Post by gaston6858 on 2010-06-10
I am unable to use card 131.  I don't think that is a valid option.  I used card 23 but I don't see video and I think the selection allows for only TV, Comp1 & Comp2.  How do you get the QLR0440 to work with zoneminder and xawtv?

---

