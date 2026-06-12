---
title: "GeForce 5200 FX TV out question"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by pjbgravely on 2008-01-01
Is it possible to run this card with 2 monitors and the S-video TV out at the same time? I can only find what this card can do, not what it can't. 

PNY version of GeForce 5200 FX
265 MB RAM
AGP  8X
Dual SVGA outputs
S-video TV output.

If anyone is running this card the way I want to, could you post your xorg.conf. I cannot seem to find one on the web, which makes me think this card isn't capable of this mode of use.

Thanks,
Paul

---

### Post by clemente on 2008-04-29
Hi pjbgravely, 

did you finally got your configuration working? 
I don't even get the tv-out with one monitor working conveniently... After fresh installation of proprietary nvidia drivers, all works well. As soon as I reboot the system, I got a blank screen. :-( 

With open source (nv) drivers, the tv out remains dark. 

If you got any success, would you share your solution? 

Thanks a lot, 
Clemente

---

### Post by pjbgravely on 2008-05-04
I discovered that the 5200 is probably the worst choice in cards for anyone wanting to use 2 monitors and TV. 

The program nvtv cannot be used for the TV out of this card. The Nvidia settings utility does work for this card. You must be using the Nvidia driver to use it. 

I was able to get nvidia-settings to switch one of my monitors to the TV and back again without a reboot of X. I was never able to do this again, for reasons unknown to me. I am planning to use this card for a DVR which when it is configured to only use TV it works very well.

If you are wanting to use this card what I found may help you. It is only able to support one monitor, and one TV at a time. Device 0 in the card can output to both VGA or TV, and device 1 can only output only to VGA. As you face the card ( from the back) the VGA output on the right of the card is device 0, the left one is device 1. 

I hope this helps.

Paul

---

### Post by clemente on 2008-05-07
Thanks a lot for your reply! Obviously not the best card... ;-) 
I finally managed to install the latest (downloaded) proprietary nvidia driver and make it surviving the reboot. 

For the archive: When installing nvidia drivers from nvidia.com, make sure that there is no nvidia kernel module installed! While booting the machine, the system loaded a nvidia module that did not work with my nvidia x-org module. I always had to manually rmmod and insmod the correct one. After deleting anything with nvidia (with apt-get and rm) the new driver works well. 

I installed the current mythbuntu 8.04 and can configure the card with the nvidia configuration tool, that mythbuntu installs by default. 

I do only use my tv - monitor is only for administration. I managed the card to run monitor and tv with cloned output - well enough for me. ;-)

Greetings, 
Clemente

---

