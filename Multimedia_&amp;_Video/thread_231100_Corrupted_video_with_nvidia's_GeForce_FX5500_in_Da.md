---
title: "Corrupted video with nvidia's GeForce FX5500 in Dapper Drake"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by nimy on 2006-08-06
I had this card working, with tseliot guidance, in Breezy Badger, however with the upgrade to Dapper Drake, the video shows a grey background where white is the norm, and text is more gray than black, which is a real eye-strain. 
I get this dmesg output:
nvidia: module license 'NVIDIA' taints kernel
Soon thereafter I get "NVRM: loading NVIDIA Linux x86 Kernel Module 1.0-8762 followed by the DTG.
dpkg -l shows these nvidia packages installed:
ii           nvidia-glx      1.0.8762_2.6.1
ii           nvidia-kernel-20051028+1 (module common files)
ii           nvidia-kernel-1.0.8762+2.6.1 (module source)
I tried installing nvidia-settings, however I have to choose between nvidia-glx and nvidia-settings: installing one removes the other.    
I've been looking through these pages for a fix, however none addresses this problem.

---

### Post by nimy on 2006-08-07
Not knowing if there's a solution to this problem, I have a work-around, which is to change the Ubuntu desktop theme to High Contrast Inverse (System -> Preferences -> Theme) so at least the menus and terminal windows are readable.  I corrected the horizontal sync and refresh rates in the monitor settings in /etc/X11/xorg.conf to match ddcprobe output for my VX900 Gateway, but still can't use the browser because gray lines of varying darkness appear on any page with a white background.  

In case tseliot or others are looking into this, here's some background information: I wasn't able to find a /usr/share/applications/NVIDIA-settings.desktop file at any time during theis upgrade, possibly due to the conflict between the nvidia glx and settings modules. 
When I run $ dpkg -l 'nvidia*' there are also five entries for:
un nvidia-kernel <none> (no description available)
and a couple of rc entries where the config files on removed packages remain, however the repeated 'un' entries look strange.
Finally, I have an older NVIDIA NV34 Board - the GeForce FX 5200, running on RHES with no problems, but that may be because RHES charges a fee for their OS.

---

### Post by tseliot on 2006-08-07
> **nimy said:**
> Not knowing if there's a solution to this problem, I have a work-around, which is to change the Ubuntu desktop theme to High Contrast Inverse (System -> Preferences -> Theme) so at least the menus and terminal windows are readable.  I corrected the horizontal sync and refresh rates in the monitor settings in /etc/X11/xorg.conf to match ddcprobe output for my VX900 Gateway, but still can't use the browser because gray lines of varying darkness appear on any page with a white background.  

In case tseliot or others are looking into this, here's some background information: I wasn't able to find a /usr/share/applications/NVIDIA-settings.desktop file at any time during theis upgrade, possibly due to the conflict between the nvidia glx and settings modules. 
When I run $ dpkg -l 'nvidia*' there are also five entries for:
un nvidia-kernel <none> (no description available)
and a couple of rc entries where the config files on removed packages remain, however the repeated 'un' entries look strange.
Finally, I have an older NVIDIA NV34 Board - the GeForce FX 5200, running on RHES with no problems, but that may be because RHES charges a fee for their OS.

You can try this command:
```
sudo apt-get install --reinstall nvidia-glx linux-restricted-modules-`uname -r` nvidia-kernel-common
```

Then log out and press CTRL+ALT+Backspace


If that doesn't work then you might try my Envy script

---

