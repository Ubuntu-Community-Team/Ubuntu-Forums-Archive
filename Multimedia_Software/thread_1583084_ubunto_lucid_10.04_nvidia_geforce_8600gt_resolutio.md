---
title: "ubunto lucid 10.04 nvidia geforce 8600gt resolution problem"
date: 2010-09-27
forum: Multimedia Software
---

### Post by Cenko on 2010-09-27
Hi,

Last week I had a PC that dual on windows and Ubuntu 9.04, and I bought a new monitor, which supports up to 1920x1080. In windows I could use that resolution but in ubuntu I was limited with something like 1280x1024. 

I have nvidia geforce 8600gt.

Two days ago I made clean install of ubuntu 10.04 by deleting the whole harddisk, hoping it would work better with my new monitor.


Unfortunately its all same. When I tried to activate nvidia driver it did not made the resolution issue better. Then I read some fixes, tried removing and installing other nvidia and nvidia-glx drivers but still it doesn't work. 

In some drivers, the resolution goes as less as 640x480 and can't be made higher.

And now, when I go to hardware drivers, for the last driver I installed, it says "This driver is activated but not currently in use"

What shall I do?

---

### Post by Hypello on 2010-09-28
I have the same problem, if not similar.

Fresh install of 10.04 (x86) with 8600GT
Chose the recommended NVIDIA drivers using jockey (Hardware Devices)

For a while, I too was stuck at 640x480 but somehow I'm currently living in 1024x768 which, according to xrandr is my max resolution. This isn't the case, I should be able to get 1280x1024.

It seems like it just won't detect the monitor properly. Whats more, I get two different lists for possible resolutions within System>Prefs>Monitor and the NVIDIA X Server Config and it seems these don't read from xorg.conf

Any help would be appreciated.

---

### Post by wtix20 on 2010-09-28
[B] i heve problem  
[/B]

---

### Post by Hypello on 2010-09-30
I found a fix... it was quite easy.

If you looked in the Xorg logs (mine were in /var/log/Xorg.0.log) you may have seen the lines:
```

(WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
(WW) NVIDIA(GPU-0):     unrecognized EDID Header.
```

Basically this means the monitor isn't feeding the information in a way the driver can understand - at least thats my interpretation.

So the fix. Make sure you have the red lines in your "Monitor" section of xorg.conf
```
Section "Monitor"
    Identifier     "Configured Monitor"
[COLOR="Red"]    Option "UseEDIDFreqs" "FALSE"
    HorizSync    22-82
    VertRefresh  56-76[/COLOR]
EndSection
```

Obviously replace those frequencies with the ones specific to your monitor. After restarting X, you should be able to access any resolutions using Nvidia X Server Settings.

---

### Post by debasishg on 2010-09-30
this might help you.....

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by realzippy on 2010-09-30
> **debasishg said:**
> this might help you.....

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```


...why should it?
Try Hypello's solution instead.

---

### Post by Cenko on 2010-09-30
Hypello! If you were here I'd buy you a huge dinner.

You solved it! Thanks a million.

---

### Post by luketongs on 2010-11-10
Yep this help me too. Thanks mate.

---

