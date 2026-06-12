---
title: "Kworld Video Magician"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by GapDragon on 2007-11-17
I've got a Kworld Video Magician (a video capture card with a drive bay mounted interface -- you can read about it here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16815100128](http://www.newegg.com/Product/Product.aspx?Item=N82E16815100128)).

I'm positive that at some point in the past I installed a version of Linux that recognized it and set it up automatically.  I believe that install recognized the core chip on the card (the name Connectix seems to stick in my brane but I don't think it's right).

Naturally, I have no idea what that Linux version was...

As far as I can tell, Ubuntu (Gutsy) has no idea this hardware is in my computer, but I have no idea how to check.  My computer is set up to dual boot and the card is working in Windows, so I know it's functioning...

Can anybody clue me in how to install software for this card or check if it is already??

Finally, I'll check the Windows configuration a post additional info to this thread...



Thanks,
GapD

---

### Post by GapDragon on 2007-11-18
I did that windows check and I was wrong...

The capture card is a Conexant TV88X, does anybody have a hint??




Thanks,
GapD

---

### Post by RedfishBluefish on 2008-04-04
Bump.
I have one of those too.

As it happens I get a message when starting up:
```
[   31.671339] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   31.671424] ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[   31.671461] cx88[0]: Your board has no valid PCI Subsystem ID and thus can't
[   31.671462] cx88[0]: be autodetected.  Please pass card=<n> insmod option to
[   31.671464] cx88[0]: workaround that.  Redirect complaints to the vendor of
[   31.671465] cx88[0]: the TV card.  Best regards,
[   31.671466] cx88[0]:         -- tux
[   31.671468] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   31.671470] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   31.671472] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   31.671474] cx88[0]:    card=2 -> GDI Black Gold
[   31.671475] cx88[0]:    card=3 -> PixelView
[   31.671477] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   31.671479] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   31.671481] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   31.671483] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   31.671485] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   31.671487] cx88[0]:    card=9 -> Leadtek PVR 2000
[   31.671488] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   31.671490] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   31.671492] cx88[0]:    card=12 -> ASUS PVR-416
[   31.671494] cx88[0]:    card=13 -> MSI TV-@nywhere
[   31.671496] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   31.671497] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   31.671499] cx88[0]:    card=16 -> KWorld LTV883RF
[   31.671501] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   31.671503] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   31.671505] cx88[0]:    card=19 -> Conexant DVB-T reference design
...(more options)

```

The official page is [here]("http://www.kworldcomputer.com/product/editing/005/Video_Magician.htm"). This card also calls itself an 883-something, so I thought I'd try doing a 'modprobe cx88xx card=16'. It didn't seem to make much difference.

So anyway.. Bump.

BTW you can list your hardware with "lspci -v".
I did that and got this:
```
05:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2
```
Which isn't really a lot of use.

EDIT:
I just went to the [wiki]("http://linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x)") . It doesn't seem like this specific card is supported at all, so I have no idea how it worked before.

---

