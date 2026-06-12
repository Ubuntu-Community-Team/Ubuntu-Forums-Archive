---
title: "DVR Card &amp; Zoneminder"
date: 2010-06-05
forum: Multimedia Software
---

### Post by browndog289 on 2010-06-05
Hello

I am stuck! Can anyone help?
I have an ubuntu 9.10 setup with zoneminder v1.24.1 installed from the repositories.

I have a generic 4 channel DVR PCI card with the following details on it:

PTK8606/P-RA
0426HTQK

CONEXANT
FUSION 878A
25878-13
0450Y1DG
0450 TAIWAN

SKY-104 05042817297 UCC4 VER 2.0 S/N: -------------

Dmesg returns:

dmesg | grep bttv
[ 22.447193] bttv: driver version 0.9.18 loaded
[ 22.447199] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 22.447266] bttv: Bt8xx card found (0).
[ 22.447290] bttv 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 22.447303] bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 18, latency: 32, mmio: 0xe3002000
[ 22.464245] bttv0: using: GrandTec Multi Capture Card (Bt878) [card=77,insmod option]
[ 22.464251] IRQ 18/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[ 22.464335] bttv0: gpio: en=00000000, out=00000000 in=00f360ff [init]
[ 54.744019] bttv0: tuner absent
[ 54.744217] bttv0: registered device video0
[ 54.744244] bttv0: registered device vbi0
[ 54.744263] bttv0: PLL: 28636363 => 35468950 .. ok
[ 73.428932] bttv0: PLL can sleep, using XTAL (28636363).
[ 73.988014] bttv0: timeout: drop=11 irq=44/657, risc=11d9c024, bits: HSYNC FDSR

From what I can see it is card type 77 which I believe is a colour card (GrandTec Multi Capture Card (Bt878) [card=77,insmod option]).

However when I run zmu -d /dev/video0 -q -v I get:

Video Capabilities
Name: BT878 video (GrandTec Multi Cap
Type: 45
Can capture
Does teletext
Overlay onto frame buffer
Can clip
Video Channels: 4
Audio Channels: 0
Maximum Width: 744
Maximum Height: 576
Minimum Width: 48
Minimum Height: 32
Window Attributes
X Offset: 0
Y Offset: 0
Width: 320
Height: 240
Picture Attributes
Palette: 1 - Linear greyscale
Colour Depth: 8
Brightness: 32768
Hue: 32768
Colour :32768
Contrast: 32768
Whiteness: 0
Channel 0 Attributes
Name: Composite0
Channel: 0
Flags: 0
Type: 2 - Camera
Format: 0 - PAL
Channel 1 Attributes
Name: Composite1
Channel: 1
Flags: 0
Type: 2 - Camera
Format: 0 - PAL
Channel 2 Attributes
Name: Composite2
Channel: 2
Flags: 0
Type: 2 - Camera
Format: 0 - PAL
Channel 3 Attributes
Name: Composite3
Channel: 3
Flags: 0
Type: 2 - Camera
Format: 0 - PAL


Which shows Type: 45 and Palette: 1 - Linear greyscale.
How can I get Zoneminder to correctly identify this card so I can capture in colour?

Thanks in advance!

---

### Post by dumb as a stump on 2012-02-06
So did you find a solution to this? Im about to try it too.

---

