---
title: "subwoofer problem on fujitsu laptop"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by stangbang on 2006-02-07
ok so here is the problem. I am using a Fujitsu Lifebook N6010 laptop, and I am not able to get any sound out of the subwoofer. The 2 side speakers work just fine, but I cant seem to be able to do anything to get the subwoofer to work.

Here are the specs for the soundcard in the laptop:
    *  SigmaTel® STAC9766 with wavetable, 3D effect, and 3D positioning (AC '97 Compliant Codec)
    * Dolby® headphone application simulates realistic surround sound using conventional stereo headphones while playing DVD movies
    * Two built-in stereo speakers and a sub-woofer

Here is the output for my /proc/asound/cards:
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with STAC9752,53 at 0x8400, irq 18

**** The STAC9766 is soposed to be 100% compatable with the STAC9752. ****

Also here is the sound card portion from lspci incase that can do any help:

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Fujitsu Limited.: Unknown device 12d0
        Flags: bus master, medium devsel, latency 173, IRQ 18
        I/O ports at 8400 [size=256]
        I/O ports at 8800 [size=128]
        Capabilities: [48] Power Management version 2



Any help, or idea's would be appreciated.

---

### Post by kd5ftn on 2006-06-26
I have an N6010 as well.

As far as i know, the subwoofer isn't a seperately controlled third channel. A hardware crossover sends the lower frequencies of the stereo audio to the sufwoofer.

Therefore, if your sub isn't working, it sounds like a hardware issue. Mine seems to work fine.

---

