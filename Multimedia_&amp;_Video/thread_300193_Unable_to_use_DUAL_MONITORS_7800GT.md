---
title: "Unable to use DUAL MONITORS 7800GT"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by keka on 2006-11-15
Hi, huys, I know this is an old topic but after trying many different aproaches I am still unable to use both monitors with nVidia 7800GT. Maybe someone can share their experience. thanks

ANd one more thing, befor i Installed nVidia-xgl, I belive i was able to use nVidia setting to it's fuill potential. I was able to use gamma and color controls,see the temp, now I don't have this? I really need to adjast display gamma.

---

### Post by emuman on 2006-11-15
Do you have installed the nvidia drivers? Try nvidia-settings. It can detect your displays and creates a working X configuration. Extract the parts you need (device and screen sections) and paste them into your xorg.conf. I attached my xorg.conf. You can use it as start point, e.g. replace

Option	   "ConnectedMonitor" "DFP, TV"
Option     "UseDisplayDevice" "DFP, TV"

with

Option	   "ConnectedMonitor" "DFP, DFP"
Option     "UseDisplayDevice" "DFP, DFP"

if you have two LCDs. I recommend '/usr/share/doc/NVIDIA_GLX-1.0/README.txt' for more information about twinview.

---

