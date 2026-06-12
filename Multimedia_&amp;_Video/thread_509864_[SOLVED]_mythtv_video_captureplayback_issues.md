---
title: "[SOLVED] mythtv video capture/playback issues"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by a_posse_ad_esse on 2007-07-25
Hey all, I am a very recent migrant from Gentoo.  I am loving Ubuntu so far, and have even converted my wife completely to Linux because of its ease-of-use. :-)

I have been fighting with configuring a home server for a long while now (as in since early December... tried Gentoo->Pluto->Ubuntu), but have just about completed its core functionality.  The print server and samba shares are working very well, and mythtv is installed and running; the only thing remaining is that the video in mythtv is garbed, and my second card isn't recognized.

I am running an older ATI TV Wonder (bt878), which is the recognized card giving the garbled output.  I have tried various "card" settings with modprobe, but none give satisfactory results.  The output for the card in lspci -v is:

```

00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: ATI Technologies Inc Unknown device 0001
        Flags: bus master, medium devsel, latency 132, IRQ 18
        Memory at e0003000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: ATI Technologies Inc TV-Wonder
        Flags: medium devsel, IRQ 18
        Memory at e0004000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

```

Any idea what the proper settings for the card would be?  I am fairly certain that this is the issue, as I had the card working very well in Gentoo about a year and a half back.

My second card is an ATI TV Wonder 200.  I saw the forum post about how to get this card working, but it doesn't seem to help mythtv recognize it.  The lspci -v output is:

```

00:0b.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: ATI Technologies Inc Unknown device 00f9
        Flags: bus master, medium devsel, latency 165, IRQ 17
        Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

```

Again, any ideas how to properly configure this card?  I am also wondering at the <access denied> portion of the output on both...

Thank you for your help on this.

---

### Post by a_posse_ad_esse on 2007-07-28
Any ideas?

---

### Post by a_posse_ad_esse on 2007-07-30
I have decided to abandon the hardware in question in favor of Hauppauge.

---

### Post by UncleJock on 2007-11-30
Please tell me did this work for you?

This is my second attempt at building an Ubuntu box, and first try at building a PVR.
I have an ATI TV Wonder, and am willing to go buy a Hauppauge 350 right away, if it'll solve my video/audio sync problem. I know the 350 has hardware encoding/decoding, and that this significantly reduces the processor load. However, I need to be sure it's just the capture card that's the bottleneck, before replacing it. The hard drives don't appear to be the problem.

The mutant box hardware:
Intel P4 1.7GHz
512M RAM
ATI TV Wonder analog capture card
ATI 9200 video card
IDE hard drives.

---

### Post by a_posse_ad_esse on 2007-11-30
Mythtv worked out-of-the-box with my Hauppauge 500,  My only issue has been, since it is a dual tuner, that the machine sometimes freezes after recording 2 shows at once.  I think that this an irw driver issue though, and is specific to the 500.

---

