---
title: "Can't get 848x480 resolution"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by Tasu on 2005-11-22
Hi all,
I have a samsung plasma tv that can go 848x480, 60Hz, this is the preferred resolution for it since it doesn't do distortions on image (i.e. everything looks fat... like icons, wider than tall! ^_^)... The video device is a Intel 865G, I installed the 855resolution package via Synaptic to change the ram bios to support 848x480, using [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) (both compiled and on line versions) modeline generator, I generated a modeline for that particular resolution and VSync and placed in the Monitor section and referred to that modeline name in the screen section ... but the X server seems not to apply it, it brings me to the desktop, but only displaying at 1024x768, 800x600 or 640x480 (and giving just those res as choices).

Furthermore... I tried elive cd, based on morphix/knoppix, at the start, during the boot, it probes for monitor, the monitor is perfectly recognised, and that utility even understands that the monitor can accept just 848x480, 800x600 and 640x480 resolutions... ok, it perfectly probes it, but it then loads the X server at 1024x768 (not supported mode... just had to do a ctrl+alt++ to switch to a mode supported by the monitor)... I assume that even ubuntu manages to perfectly probe that 848x480 resolution, but can't aplly it for some reasons.. why?

Thanx for the answer,
Sorry for my english

Tasu

---

### Post by Teroedni on 2005-11-22
I dident quite understand what your after
Do you want to get 848x480 working?

---

### Post by Tasu on 2005-11-22
yes, I just want my 848x480 work, but nothing seems to change whatever i do, gnome resolution application shows me just 1024x768, 800x600, 640x480 (and 1024x768 is not even supported by the plasma tv! O_O)

Thanx for the answer

---

