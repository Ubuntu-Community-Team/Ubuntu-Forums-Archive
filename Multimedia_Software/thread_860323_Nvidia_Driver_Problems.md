---
title: "Nvidia Driver Problems"
date: 2008-07-15
forum: Multimedia Software
---

### Post by minime283 on 2008-07-15
Sorry for cross posting.. this might be a better area.

I'm new to Ubuntu. So I setup my computer with two monitors through the Nvidia Drivers (Geforce 7600GT) and I was having a few minor issues with it, so I switched over from the glx-Nvidia-new drivers to the glx-nvidia-new-envy drivers and That pretty much broke the drivers. When I try to run sudo nvidia-settings from the command line it tells me to run nvidia-xconfig as root and restart the X server. I've done this and it doesn't work. The closest I got was copying over the xorg.conf from the livecd to my /etc/X11/ folder gets my computer back into an alright resolution, but when I try to activate the Nvidia drivers through the Hardware Manager it breaks again. I've tried uninstalling and reinstalling all the driver stuff in Synaptic but that didn't work either. I'm attaching my xorg.conf below.

---

