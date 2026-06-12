---
title: "resolution with nvidia driver"
date: 2009-08-25
forum: Multimedia Software
---

### Post by travisgerard on 2009-08-25
Alright, I'm at a lost with trying to fix this problem... I'm using the onboard video of ECS GF8200A motherboard (HDMI connected to my 26 hdtv). Before I install the nvidia driver, the screen looks fine - it has about a 1/2 inch black border and everything is readable. After the install, the border is gone and I can't view roughly 1/2 - 1 inch of the screen on all sides. Is there anyway to fix this without removing the driver?

Thanks for the help :)

---

### Post by travisgerard on 2009-08-25
no suggestions from anyone :confused:

---

### Post by RedSingularity on 2009-08-25
What does your **/etc/X11/xorg.conf** look like?

---

### Post by travisgerard on 2009-08-25
Now the driver is causing some other problems.  Before I get the chance to copy the info here the screen scrambles or just turns bright orange and the comp freezes.

xorg.conf said something along the lines of 

Section "Monitor"
Identifier "Configured monitor"

Section "Screen"
Identifier "Default screen"
Monitor "Configured monitor"
Device "Configured Video Device"
DeaultDepth 24

Section "Module"
Load "glx"

Section "Device"
Identifier "Configured video device"
Driver "nvidia"
Option "NoLogo" "True"

I'm thinking that I might just be out of luck because its causing the comp to freeze up...?

---

### Post by RedSingularity on 2009-08-25
Well you could always use the open source drivers that come installed.  They don't support 3D rendering yet but it is usable.  If you want to go back to the original drivers just boot into a text interface and type this in to remove the proprietary drivers.

```
sudo apt-get autoremove nvidia-glx-180
```

Then reboot.

---

### Post by peepingtom on 2009-08-26
^^Forget that! He should use the binary drivers, he paid for a 3d-accelerating card after all!
The fact is that many cheaper 720p and 1080p screens have flaws at the edges, so the plastic bezel covers about an inch of the screen all around. Have you tried running ```
sudo nvidia-settings
``` and autodetecting the resolution of the screen? It's likely a bit of an oddball resolution that will be detected via DPMS. I ran into this issue on my friend's Sony TV, this is the only solution because it's a physical geometry on the TV. Hope this works for you!

Tell us the model of your TV, or google around and find its native resolution. I bet it's weird! 

Edit: Corruption, eh? Try using the latest Nvidia Drivers from this PPA, I believe it's official.
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)
Make sure to remove the old ones and install glx 185 (190 is beta) and the right nvidia-setting package. Good luck, we're ready to help you.

---

