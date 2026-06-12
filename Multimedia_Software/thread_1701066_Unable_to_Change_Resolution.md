---
title: "Unable to Change Resolution"
date: 2011-03-06
forum: Multimedia Software
---

### Post by Suikoden on 2011-03-06
I'm currently using ubuntu 10.04 version. I've recently purchased a BenQ E2200HD monitor. However, the monitor is unable to configure a resolution higher than 800x600. I've tried changing it via 'preferences' - 'monitor' etc. The monitor model is 'unknown'. and the highest resolution available is the 800x600. 

I've tried changing it manually, but it says x.cong file does not exist. Xrandr doesnt seem to work either. Or i would get CTRC 262.

My current set up is, intel i5 2600, 4GB Ram, Nvidia GTS 240. I'm pretty certain, my graphics card (despite being in the low end) can support HD resolution. Even if it can't, it surely can support a resolution higher than 800x600. 

Please help me out here! I've spent hours trying to manually configure the resolution and I'm completely stuck!

---

### Post by johntaylor1887 on 2011-03-06
Did you install the Nvidia drivers? Go to *System*>*Administration*>*Hardware Drivers* and install the nvidia current drivers and reboot.

---

### Post by Yellow Pasque on 2011-03-06
> **johntaylor1887 said:**
> Did you install the Nvidia drivers? Go to *System*>*Administration*>*Additional Drivers* and install the nvidia current drivers and reboot.
Usually, that would be the easiest way, but the drivers that came with Lucid probably don't have had support for the GT240 in them. Using this PPA will give the latest nvidia driver for Lucid without touching the rest of the graphics stack: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)

---

### Post by Suikoden on 2011-03-06
i inserted the nvidia drivers disk..which file do i use...they're only for window vista and 7. I tried doing "system" - 'admin'- ' hardware'-'driver' but none were detected...im feeling ultra noob atm

---

### Post by Yellow Pasque on 2011-03-06
LOL. I'm not sure how you got that idea out of my post. Let me make it dead simple:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers
```

---

### Post by Suikoden on 2011-03-06
says 'couldn't find package nvidia-graphics-drivers'

---

### Post by johntaylor1887 on 2011-03-06
> **Suikoden said:**
> says 'couldn't find package nvidia-graphics-drivers'

Do:
```
sudo apt-get install nvidia-current
```

---

### Post by Suikoden on 2011-03-07
got it to work! the problem was because ubuntu can't detect nvidia drivers via vga cables. i had to swtich to dvi, and then update with ppa. and now x.config and xrandr both work! Thanks guys!

---

