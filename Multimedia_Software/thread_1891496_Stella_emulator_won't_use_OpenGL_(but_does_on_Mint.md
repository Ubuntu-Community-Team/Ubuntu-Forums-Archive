---
title: "Stella emulator won't use OpenGL (but does on Mint) -- nvidia driver works"
date: 2011-12-05
forum: Multimedia Software
---

### Post by mrowth on 2011-12-05
The Atari VCS emulator Stella (3.4.1, package from Ubuntu repositories) falls back to software rendering every time on my Kubuntu 11.10 system. 

It used to work in the past and still works on Mint 12. 

glxgears works, kwin desktop effects work great, other emulators with similar visual effects work (PAL colour loss, scanlines). I can play relatively demanding 3D games like the Penumbra series.

Nvidia drivers 280.13-0ubuntu6 (package nvidia-current) are installed and running. I deleted my xorg.conf and let nvidia-xconfig create a new one. I also deleted ~/.nvidia-settings-rc. And I disabled all optional effects in Stella. All to no avail, obviously. 

Posting this on the off chance that anyone's using Stella here and has an idea...

:o

---

### Post by inobe on 2011-12-05
not using stella, maybe giving the 290 a try?

adding the x-swat ppa will get you the 290 drivers [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric)

---

### Post by mrowth on 2011-12-05
That doesn't make a difference, but thanks for the ppa!

---

