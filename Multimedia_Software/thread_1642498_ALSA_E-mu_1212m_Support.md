---
title: "ALSA E-mu 1212m Support"
date: 2010-12-10
forum: Multimedia Software
---

### Post by nruggeri on 2010-12-10
Hey guys,

I'm trying to check on ALSA support for the E-mu 1212m PCIE sound card.  It appears to be supported hardware, and it looks like a few people are using it.

In terms of functionality; are people able to capture 48khz 8-channel ADAT (16bits? 24 bits?) and use hardware-accelerated mixing?  That's really all I think I need from the card.

If you have suggestions for cheaper supported cards that do the same, I'd love to hear that too!

-- Ned Ruggeri

---

### Post by cchhrriiss121212 on 2010-12-10
Hi Ned.
According to the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") ADAT is supported on the emu 1212m, but the PCIe version has an unknown tag meaning it has not been officially tested. I would try it out before buying one if possible. This page is also worth a read:
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1#comments](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1#comments)

I don't think there are any cards cheaper than the 1212m with ADAT. I only know of the RME HDSP line, which are a bit more pricey. 

I can't seem to find any info on hardware-accelerated mixing.

---

### Post by nruggeri on 2010-12-10
Thanks!

I suppose the primary use is to do multitrack recording to disk, which seems to work fine.  I would have liked to mix the audio in real-time and send it back out to the foldback, but I guess I'll have to hope to get enough CPU to do that...

---

