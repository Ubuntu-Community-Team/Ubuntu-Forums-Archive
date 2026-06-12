---
title: "asfxload stuck at 8MB limit."
date: 2013-07-30
forum: Multimedia Software
---

### Post by SweetAurora on 2013-07-30
Hi, I'm trying to load a 32MB sound font into ram so I can get sweet midi tunes out of my EMU10k1, but for some reason, asfxload will not load a font larger than 8MB. I know the EMU10k1 can use a 32MB font, and I read that asfxload can load fonts that big, but for some reason, it won't. Help please?

Edit: Nevermind, found out the reason. The EMU10k1 has a wierd memory address size, (31Bit) as well as only being able to have DMA to the first 2GB of ram. My PC has 4GB of ram. So when the card asks for space in the memory, the EMU10k1, memory controller, and Kernel get confused and instead settle on giving the EMU10k1 access to the ISA memory range of 16MB. Hence why my 8MB font fits, but not my 32MB font. Only solution I found was to rebuild the kernel from source and set a config parameter for the DMA only allowed to access the first 2GB of ram, fixing the confusion and allowing a bigger than 16MB font. Oh well...

---

