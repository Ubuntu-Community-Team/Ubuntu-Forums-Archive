---
title: "Activate framebuffer tridentfb on console during bootup"
date: 2010-11-16
forum: Multimedia Software
---

### Post by MrStarbuck83 on 2010-11-16
Hi everyone!

I have a problem activating the framebuffer driver *tridentfb* using kernel boot options. This is my (onboard) graphics card as shown by *lspci*:

```
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)
```I am using 10.10 server and configured grub2 to pass the following command line:

```
video=tridentfb:800x600
```Nothing happens, after boot I am still in normal text mode, 80x25 or something like that.

I also tried specifying the bit depth and refresh rate by passing *video=tridentfb:800x600-16@60* without any luck.

When I load the module manually by typing *modprobe fbcon && modprobe tridentfb* everything works fine, but I want to activate it during bootup. I checked system logs for any error message - none, although the kernel command line is correct as seen here:

[http://www.mjmwired.net/kernel/Documentation/fb/tridentfb.txt](http://www.mjmwired.net/kernel/Documentation/fb/tridentfb.txt)

Btw, *vga=791* works, but I want the trident driver, since it's faster and works better for me, because page scrolling (for example in *man* or *vi*) would become very slow with vesa generic driver.

What am I missing?

Grateful for any advice

- Starbuck

---

