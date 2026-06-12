---
title: "Grub resolution+2.6.14.4"
date: 2005-12-20
forum: Multimedia &amp; Video
---

### Post by luminoso on 2005-12-20
Hi..
I have ubuntu 2.6.14.4+cK7 kernel, Nvidia Geforce FX 5600 and a Intel Pentium4 CPU.
My kernel is configured according to this:

> 
<*> Support for frame buffer devices
 
[*]   Enable Video Mode Handling Helpers
 
[*]   Enable Tile Blitting Support
 <*>   VGA 16-color graphics support
 [*]   VESA VGA graphics support
 < >   nVidia Framebuffer Support
 < >   nVidia Riva support


> 
Console display driver support
 [*] VGA text console
 [*]   Video mode selection support
 <M> MDA text console (dual-headed) (EXPERIMENTAL)
 <*> Framebuffer Console support
 [*] Select compiled-in fonts
 [ ]   VGA 8x8 font
 [*]   VGA 8x16 font


I also edited my /boot/grub/menu.lst acording to this table:

> 
         640x480    800x600  1024x768 1280x1024
256    0x301       0x303      0x305      0x307
32k    0x310       0x313      0x316      0x319
64k    0x311       0x314      0x317      0x31A
16M   0x312       0x315      0x318      0x31B


So.. my menu.lst is:

> 
title           Ubuntu, kernel 2.6.14.4
root            (hd0,0)
kernel          /vmlinuz-2.6.14.4 root=/dev/mapper/Ubuntu-root ro quiet vga=0x31B
initrd          /initrd.img-2.6.14.4
savedefault
boot


The problem is that i got a black screen when everything is loading, and only get imagem when GDM loads.
I also tried to install a kernel with Nvidia Framebuffer Support enabled on kernel, and i got 1280*1024 resolutiom, but when installing nvidia official drivers(81.74) it says that i can't have nvidiafb compiled.
Even after reinstall of nvidia drivers after new kernel installation i dont have image when loading kernel.

Without "vga=xxx" option everything works, but in a very low resolution.


Thanks for all,
Sorry Bad english.

Guilherme

---

