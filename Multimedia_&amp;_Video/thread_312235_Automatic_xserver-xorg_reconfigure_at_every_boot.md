---
title: "Automatic xserver-xorg reconfigure at every boot"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by jdpipe on 2006-12-04
Hi there

I have a USB hard drive with Ubuntu 6.10 installed. I boot it on several different machine almost every day. Each time I move to a different machine, I need to run the 'dpkg-reconfigure xserver-xorg' script, which is a bit of a pain, especially given that all I do on every one of these different machines is to accept the defaults that it offers.

I use machines with NVidia, SIS, ATI and Intel video chips/cards.

Is there any way that instead of the X server showing an error on bootup that it instead attempt to autodetect the correct settings? Could anyone suggest how I might do that?

A further complication (but not so serious) is that although some of these systems will support hardware OpenGL, i must use Mesa3D on all of them, because of the way that the Debian packages are set up. Maybe some suggestions on this as well?

Cheers
JP

---

### Post by Jimmey on 2006-12-04
Just set xorg's driver to "Vesa". That should work with any graphics devices. If you want 3D acceleration after that, you'll need to reconfigure xorg. But Vesa should work alright on all of them ;-)

---

### Post by jdpipe on 2006-12-04
Hi there

Wondering what the basis is for your suggestion? Is VESA some sort of generic/base-level standard?

What about the fact that different screens support different resolutions, colour depths, etc? It still seems to me that some degree of reconfiguration is still required, but I had hoped that it might be automatable.

Also note that on the ATI video card that is present on one of my machines, the white/orange on black "Ubuntu" splash screen doesn't show up, due to unsupported resolution settings.

Cheers
JP

---

