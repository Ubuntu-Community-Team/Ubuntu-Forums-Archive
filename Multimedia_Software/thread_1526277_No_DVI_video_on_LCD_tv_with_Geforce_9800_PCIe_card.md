---
title: "No DVI video on LCD tv with Geforce 9800 PCIe card"
date: 2010-07-07
forum: Multimedia Software
---

### Post by kudude on 2010-07-07
I've just put together a computer with a 
```
$ lspci | grep nvidia -i
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

```I've enabled the hardware driver support and when I open "nvidia-settings" with a monitor plugged into the VGA port and LCD tv (VIZIO) plugged in from the DVI -> HDMI port I only see the one VGA monitor.  The tv isn't displayed whatsoever.

After clicking "detect displays" this is all I get:


[IMG]http://i153.photobucket.com/albums/s240/jnoffsinger/Screenshot.png[/IMG]

the weird thing is it was working at first, and then I upgraded the distro and added compiz (possibly did a bunch of other things), restarted and now nothing.

thanks in advance for any advice

---

