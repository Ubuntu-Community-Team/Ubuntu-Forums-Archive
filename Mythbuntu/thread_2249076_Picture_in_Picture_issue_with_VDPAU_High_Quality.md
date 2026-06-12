---
title: "Picture in Picture issue with VDPAU High Quality"
date: 2014-10-19
forum: Mythbuntu
---

### Post by whosmatt on 2014-10-19
Just upgraded my box with a Geforce GT610 fanless card.  VDPAU playback works wonderfully, taking a huge load off the rest of the system.  One glitch, though, is that when I open a PIP, the small window simply shows a frozen garbled display until I swap windows, after which both work fine, with smooth and clear playback.  Anyone else notice this?

Matt

---

### Post by MrBackhand on 2014-10-24
NVidia has this option disabled.  You can read up on it @ [https://www.mythtv.org/wiki/VDPAU](https://www.mythtv.org/wiki/VDPAU).  If you disable VDPAU and have software rendering the PiP mode will work.  I tried it, it does work, but I did switch back to VDPAU.

Some highlights/limitations of NVIDIA's current implementation:


Supported on NVIDIA GPUs with the NVIDIA second generation video processors (see list further below)
Currently, only one video stream can be decoded at a time; NVIDIA hopes to lift this restriction eventually.

Hope this helps!

MrB

---

