---
title: "[SOLVED] Issues with ALSA"
date: 2008-11-28
forum: Multimedia Software
---

### Post by RPG Master on 2008-11-28
Two days ago I had to transfer 30gigs of data to a family members laptop. After that I had to shut it down. When I did, the screen hung at a black screen with text along the lines of: "shutting down ALSA" so I had to hold down the power button. Then when I turned it on later that day, instead of the normal boot-up sound I got a bunch of static. After setting all my audio to use OSS I am able to listen to music but OSS isn't exactly ideal...
Anyone know how to get my ALSA working again?

---

### Post by markbuntu on 2008-11-28
You can try reinstalling alsa:

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop may also be removed in this process if you are using Gnome and Hardy 8.04 so watch for messages about that and other packages that are removed in the terminal. If gdm and ubuntu-desktop need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

If you are using xubuntu gdm and xubuntu-desktop may be removed
```

sudo apt-get install gdm xubuntu-desktop

```

---

### Post by RPG Master on 2008-11-28
I put in the commands and now I don't even hear static.
I'll try a reboot.

---

