---
title: "P5N7A-VM HDMI output gets a blank screen"
date: 2009-09-16
forum: Multimedia Software
---

### Post by pelesl on 2009-09-16
I installed Mythbuntu 9.04 about a month ago on a P5N7A-VM (GeForce 9300 on-board). The video card has VGA, HDMI, and DisplayPort. When I first installed it I hooked it up to my HDTV via VGA. Now I bought an HDMI cable, and when I boot up, I can see graphics on the HDMI input of the TV (system post, Mythbuntu startup screen) but once I'm in X, I just get a blank screen.

If I hook up the VGA and boot, then the HDMI input of course gets no signal.

With the VGA plugged in, nvidia-settings shows my display on "CRT-0". If I change it to "DFP-0", I see the blank screen on the HDMI input, so at least something is going over there.

The NVidia driver is 180.44. xorg.conf is whatever gets spit out when you install that driver.

Seems like no one else is having this problem, because I've searched up and down and got nothing, so I must be a dumbass. Really I'm getting too old to fight Linux on things like this.

---

### Post by blackketter on 2009-10-30
I had a very similar problem after installing the NVidia drivers on my Acer Apire Revo on Ubuntu 9.10.   The HDMI input on my Dell s2409w monitor would go black (and lock up the monitor) until I unplugged the HDMI.  VGA worked fine, just like you saw.

Alas, I don't have a solution for you, but I did figure out a workaround.

My workaround was to use an HDMI to DVI cable and the DVI input on my monitor.  The HDMI input is now being used with my MacBook Pro with no problems at 1080p.

---

