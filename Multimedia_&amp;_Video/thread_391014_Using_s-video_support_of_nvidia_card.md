---
title: "Using s-video support of nvidia card"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by Dylock on 2007-03-22
howdy

alright well my s-video cable came in today and made the bold attempt of seeing if hooking up s-video jacks between the computer and tv would work and of course it did not. So what all needs to be done to display video through the s-video to the tv.

I have an nvidia card, and running edgy.

thanks
dylock

---

### Post by tseliot on 2007-03-22
Install the Nvidia driver via Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

then type:
```
sudo nvidia-settings
```

Click on the "X Server Display Configuration" section and set the tv-out from there

---

### Post by rbm0307 on 2007-03-22
The thread in the Tips forums called [ **[COLOR="RoyalBlue"]HOWTO: NVIDIA TV-OUT for Newbies[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv+howto") gives you all the information that you are searching for.  As an additional note, installing and configuring the nvtv utility will help you to find the correct configuration settings.

---

### Post by Dylock on 2007-03-22
well i started downloading and installing the nvidia driver via envy. I let it automatically configure my xconf file and proceded to restart.  Now it won't load up X with the follwoing errors:
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but this X module has the version 1.0-8776. Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly
(EE) Screen(s) found, but none have a usable configuration

I don't know when the last time I made a backup of my config file but I have no way of even getting to a terminal. Any suggestions?

---

### Post by Dylock on 2007-03-22
ok I got into the ubuntu recovery mode but Im going to need some guidance as to what I need to do. Sounds like X needs to be updated? But my question is from where/how do I update

---

