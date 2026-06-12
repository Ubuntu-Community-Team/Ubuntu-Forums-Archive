---
title: "Blank screen, 800x600 resolution for IPS monitor with nvidia graphics"
date: 2013-02-08
forum: Multimedia Software
---

### Post by dhasenan on 2013-02-08
I'm on Quantal right now, and I just got an irun ZT-SH270QHD monitor supporting resolutions up to 2560x1440.

The nvidia and nouveau drivers detect this monitor as being present. They only offer 800x600 as a resolution option. When I activate the monitor, the backlight turns on, but the screen remains blank. While I can move my cursor to that monitor, it doesn't show up.

nvidia-settings on the 304.43 driver gets pretty much zero information on the monitor (chip location, signal as TMDS, dual link connection). On the 310.14 driver, it additionally gets the native resolution as 640x480.

When I connect the monitor to a Windows computer, it works as expected. In a tty, the monitor works as expected. The monitor is functional. The computer works with another monitor I have using the same type of cable (I've swapped cables, just in case).

I have attempted forcing the resolution to change with xrandr to no effect. I have switched to the nouveau driver to no effect. I have switched which port I use for this monitor to no effect.

I'm not sure what to poke next. Recommendations?

---

