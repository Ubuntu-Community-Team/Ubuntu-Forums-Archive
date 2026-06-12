---
title: "ati x300 vram problem?"
date: 2008-12-23
forum: Multimedia Software
---

### Post by teddmeister2 on 2008-12-23
I used the following command:
```
 grep -i ram /var/log/Xorg.0.log; grep -i mem /var/log/Xorg.0.log
```
and got something confusing to me in the output:
```
(II) RADEON(0): Detected total video RAM=32768K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 32768 kByte (64 bit DDR SDRAM)

```
Does this mean that I actually have a lot more video ram that I can't access?  If so how do I access it?  If it doesn't mean that, what does it mean?  Thanks for the help.

---

### Post by teddmeister2 on 2008-12-23
nevermind.  I think I figured it out.  Apparently the chip is capable of addressing 128mb but the actual video card has only 32 mb of vram.
(Also, read the fine print when you buy a dell system; it wasn't until today that I realized that my "64mb ati x300" that I purchased with my system is actually just a card with 32 mb of vram which uses 32 mb of the system memory)

---

