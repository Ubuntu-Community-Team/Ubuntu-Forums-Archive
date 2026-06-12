---
title: "mplayer svgalib output?"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Rasputin_III on 2007-07-19
I was wondering if anyone knew whether svgalib output had been dropped from the feisty (and earlier?) mplayer package?

mplayer -vo help doesn't list it, there are no svga libraries anywhere that mplayer knows about, and of course ldd `which mplayer` doesn't mention anything either (probably redundant anyway, with the -vo help)...

mplayer doesn't automagically utilize the libraries when installed separately, and they aren't listed as a dependency (although the package description still says it is supported).

Thanks,

Ras

---

