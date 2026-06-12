---
title: "Switching from open-source ATI to proprietary NVidia drivers"
date: 2009-06-04
forum: Multimedia Software
---

### Post by Entropy_Sam on 2009-06-04
Hi there,

I've just switched graphics cards from an old-ish ATi card (no longer supported by the proprietary drivers) to a newer nVidia card.

I've had to swap these two cards around before (the nVidia one was faulty the first time around, so I've replaced it) and last time, I was simply able to select the nVidia driver in Jockey to install it.

This time, however, the change in hardware hasn't been automatically detected (possibly because I manually updated the open-source ATi drivers from source?), and Jockey isn't helping me by suggesting the nVidia drivers, so I need to take one of two actions:

a) Uninstall the open source ATI drivers and install the nVidia drivers manually. (I downloaded the nVidia binaries a moment ago, and the install program requested that I shut down my X server and start again. I tried logging out, switching to tty1 and running it from there but I had the same message - and if I do get that running, I still need to uninstall the open-source drivers, but I don't know what they are called... X-D)

b) Fix whatever is preventing Ubuntu from auto-detecting the change and have it 'hold my hand' through the configuration change.

I'd be happy to take either route, as I'll learn something either way. Any advice would be much appreciated.

Thanks!

---

### Post by Entropy_Sam on 2009-06-04
Here's my xorg.conf file. Nothing useful there...

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2304 1182
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection


```

---

### Post by Entropy_Sam on 2009-06-04
Bump :-s

Is this in the wrong forum?

---

### Post by Entropy_Sam on 2009-06-05
*sigh*

Never mind - I figured it out myself in the end.

For anyone with the same problem, here's what I did:

- Opened Synaptic Package Manager, searched "ati" and marked for removal all the x-server-xorg-video-ati/radeon drivers I had installed (4 with similar names, in total).

- Closed all applications, went to tty1 (Ctrl + Alt + F1) logged in and typed...
```
sudo /etc/init.d/gdm stop
```...to stop the X-Server.

- changed to the directory where I'd downloaded the drivers to - in my case, it was...```
cd ~/Documents/
```- Then typed ```
sudo ./NVIDIA-XXXXXXXX
```(actually, I used Tab-autocomplete (i.e. just press tab) after typing the first from letters of "NVIDIA" and it completed the filename for me) to run the installer.

- Doesn't matter if it can't connect the the nVidia site (probably won't be able to) - the installer can probably compile any extra binaries it requires (or it could in my case).

- After returning to the console, I typed... ```
sudo /etc/init.d/gdm restart
```...to restart the X-Server

- Finally, after logging in, I hit Alt+F2 and typed ```
sudo nvidia-settings
``` to set up the display.

The driver still doesn't appear in Jockey, but now I know how to update it manually, I don't need Jockey...

---

### Post by benphane on 2009-06-05
Entropy_Sam:

Thanks for posting this.   Been a while since I wanted it but, where did the "Thanks"  for the post button go?  Seem a good thing to me.

---

### Post by overdrank on 2009-06-05
> **benphane said:**
> Entropy_Sam:

Thanks for posting this.   Been a while since I wanted it but, where did the "Thanks"  for the post button go?  Seem a good thing to me.

The thanks and solved features have been disabled for forum stability.

---

