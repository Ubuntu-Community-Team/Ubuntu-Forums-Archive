---
title: "XServer won't start after changing from ATI to nVidia"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by Josh1 on 2007-01-10
Hi all,

I installed Ubuntu Edgy on my brothers computer last night (finally got him to switch to linux!) using an ATI Radeon 9250 128mb but didn't install the drivers.

After all the games were installed, he having everything running smoothly, I decided to give him my old nVidia 6600le 256mb video card so he can play games better (and the nvidia works better in ubuntu then the ati card).

So I turn off the computer, unplug the ATI and then plug in the nvidia, all goes well (detected by bios) ubuntu loads up but before i get to the login screen, a window comes up saying that x won't start.

No worries, as I thought "I will just type in:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
But it won't work.. then I think "What if I try to install the nVidia drivers?" so after 20 seconds of searching on the forums, I type in:
```

sudo aptitude install nvidia-glx

```
All goes well, installs and looks fine. I then try startx, won't load the UI. No problems, I'll just edit "/etc/X11/xorg.conf" changing nv to nVidia.

Shock and horror, it says that the 9250 (well it says 9200 lol) still appears in here... any ideas?

- Josh1

---

### Post by Josh1 on 2007-01-10
bump.

---

### Post by tseliot on 2007-01-11
uninstall the fglrx driver first. Then install nvidia-glx.

P.S. don't care about how the card is detected in your /etc/X11/xorg.con

---

