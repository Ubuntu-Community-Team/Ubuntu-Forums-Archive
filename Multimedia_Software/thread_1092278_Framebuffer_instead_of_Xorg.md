---
title: "Framebuffer instead of Xorg"
date: 2009-03-10
forum: Multimedia Software
---

### Post by maddis on 2009-03-10
I have couple programs that want to use directly framebuffer instead of Xorg. 

I installed intelfb - module and it seems thta it recognized chipset correctly. I have 855GME chipset. The problem now is that there are no /dev/fb0 so I created one with command: mknod /dev/fb0 c 29 0. This doesn't seem to be right since for example fbset says 'open /dev/fb0: no such device'. 

If I install vga16fb, I get /dev/fb0 automatically and fbset works with it too, but it only supports VGA-resolution and 16 colours so no good. I looked major and minor number from that fb0 - device node.

Any idea what might be the correct major/minor for intelfb or what else could be wrong? Although I found those same major/minor for intelfb when looked through internet.

---

