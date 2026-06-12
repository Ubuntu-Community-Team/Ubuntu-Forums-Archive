---
title: "Which nVidia drivers should I install for Ubuntu?"
date: 2012-01-24
forum: Multimedia Software
---

### Post by TheNerdAL on 2012-01-24
I got a new GPU and I wanted to install drivers for it. I noticed I have the same recommended drivers using the Additional Devices. 

I also notice a better experience with Gnome Shell. For example with i pressed the home button, it would lag with my old 8400 GS card. 

Now it doesn't

Just wondering what drivers I should get. 

Also. **_I FINALLY CAN WATCH YOUTUBE VIDEOS FULL SCREEN! _**

---

### Post by mips on 2012-01-25
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings

```

REBOOT




.

---

### Post by overdrank on 2012-01-25
Moved to Multimedia & Video

---

### Post by TheNerdAL on 2012-01-25
> **mips said:**
> ```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings

```

REBOOT




.

Done. Thanks!

---

### Post by Redflea on 2012-01-26
> **mips said:**
> ```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings

```REBOOT

.

I used the System>Administration>Hardware Drivers option from the GUI menu (10.04.3 32bit) and it downloaded and installed the nVidia drivers, but my system would not boot normally after - the screen was actually positioned so that the right edge of the window was in the middle, and I had to move my mouse to the right off screen to get it to appear on the left side of my screen in the right half of the split-window, if you get what I mean.

Anyway, is using the commands above any different from the GUI options I chose?

Is there a troubleshooting step/tweak to get the Nvidia drivers to work?

I have a Sony laptop w/nvidia geforce 310/320/330 series.

---

### Post by Redflea on 2012-01-27
Started a new thread w/my q.

---

