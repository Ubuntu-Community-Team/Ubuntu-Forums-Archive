---
title: "my resolution is incorrect from new graphics driver installation"
date: 2010-04-06
forum: Multimedia Software
---

### Post by haxxxorz21 on 2010-04-06
i just installed the driver for my nvidia card in karmic.  after i rebooted, my resolution got reset to 640x480!  i cant set it back to my monitors regular resolution and its all just getting real frusturating.

---

### Post by tommcd on 2010-04-06
Are you sure the driver is enabled properly? Open a terminal (applications > accessories > terminal) and run:
```
 glxinfo | grep -i direct

```
It should report: [B]direct rendering: Yes
[/B]

Make sure you have **nvidia-settings** installed. Just install nvidia-settings from synaptic or apt-get if you don't nave it. 
Then launch nvidia-settings with sudo:
```
sudo nvidia-settings
```
and see if you can set the proper resolution.
Then try logging out and back in, or reboot, and see if it is fixed.
What resolution were you getting before you installed the nvidia driver?
Where did you get the driver? Which driver is it? What nvidia card do you have? And how did you install and enable the driver?

And welcome to the Ubuntu forums!

---

### Post by diesch on 2010-04-06
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) may help

---

