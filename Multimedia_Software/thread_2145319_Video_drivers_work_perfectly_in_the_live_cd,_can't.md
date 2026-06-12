---
title: "Video drivers work perfectly in the live cd, can't adjust brightness after install"
date: 2013-05-15
forum: Multimedia Software
---

### Post by HappyLifeMachine on 2013-05-15
I'm on a Macbook Pro 6-2 (mid 2010), xubuntu 13.04. The problem is the screen looks very dull and I cannot adjust the brightness (the brightness indicator pops up but the screen doesn't actually adjust). Ubuntu community help wiki stated that this is a video driver issue, so I tried to install Nvidia 310 drivers but I just get a black screen when booting xubuntu.

It was suggested that the open source drivers, the drivers  in the live cd, work and are conflicting with proprietary drivers that  are installed after installation. If so, how do I remove these proprietary drivers? 

Any other ideas?
[B]
Update:[/B] It's come to my attention that this laptop uses optimus:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216M [GeForce GT 330M] (rev a2)

```

And I'm guessing that this is the reason why everything crashes? Anything I can do?




**Update 2: **I've installed bumblebee. Now I boot xubuntu, the loading screen appears without any graphical distortion! ..But then it boots into a command prompt and not my desktop environment? I thought this might be because I don't have the Nvidia drivers, so I tried to ```
sudo apt-get install nvidia-current nvidia-settings
``` but the command line said I already have these installed (probably from bumblebee).. What next?




**Update 3: **Okay, so I've now tried ```
startx
``` at the command line that for some reason boots at startup... I get a bunch of text but I believe this is the important stuff:

```
NVIDIA: could not open device file /dev/nvidiact1 (no such file or address)

Fatal Server Error: No screens found
(EE)

```

Sigh, so more nvidia issues. Am I just doomed to not being able to get Ubuntu up and running on this laptop?

---

### Post by dentaku65 on 2013-05-16
Hi,

I suppose that you installed bumblebee via PPA (sorry I'm not experienced on nVidia); if so try to revert the installation:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:bumblebee/stable
```
In this way you should have back the driver from the distribution

For the functional keys seems that Xubuntu (or Xfce 4.10/4.12) is not able to manage them natively; I suggest to solve in this way:
```
sudo apt-get install gnome-settings-daemon
```
Reboot.
Then under Setting manager -> Session and Startup -> Application Autostart
> Enable Gnome Settings Daemon
Disable XFCE Volume Daemon
In  Setting manager -> Keyboard -> Application Shortcuts
> Remove the shortcuts sets for xfce4-display-settings
Reboot. Done.

---

