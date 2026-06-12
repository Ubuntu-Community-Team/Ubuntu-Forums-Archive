---
title: "capture audio with an avermedia 4 port audio/video card"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by 4dplane on 2007-11-23
I have an Avermedia 4 port capture card, it looks like this: 
[http://www.holm-teknik.dk/lx5004/lx5004.jpg](http://www.holm-teknik.dk/lx5004/lx5004.jpg)

I am able to capture video on all for ports of this card, but I would like to be able to capture audio with this card and I have no idea how this is done.

here is a part of my lspci -v:

  02:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (                              rev 11)
        Flags: bus master, medium devsel, latency 132, IRQ 11
        Memory at f0204000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

02:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11                              )
        Flags: medium devsel, IRQ 11
        Memory at f0205000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

This card does seem to have audio capturing.

I have xawTv and the video captures just fine but there is no audio. How do I tell xawTv to listen to port two of the capture card for audio? 

How do I tell any program to capture audio on any port?

This card works with the bttv and bt878 mods.

Thanks,
4dplane

---

