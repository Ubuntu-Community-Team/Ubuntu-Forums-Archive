---
title: "Safe Graphics Mode"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Magic02 on 2007-10-22
When i updated to 7.10 and try to start Ubuntu it will only start in safe graphics mode where as before i updated it was working okay.My video card is a FX5200.When i go to change the display i only have two options 800x600 or 640x480 and it says the driver is the vesa driver.

---

### Post by dabl on 2007-10-22
You have choices.

You could re-run the dpkg reconfiguration script, and choose the nv driver, if you want to stay open source.

```
sudo dpkg-reconfigure xserver-xorg
```


Or you could install the Nvidia proprietary driver if you want to get the most performance out of your chip.  I use the Envy installer, which you can download and install from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It will automatically detect your chip and install the latest Nvidia driver that will run it.


If you'd rather go for the packaged driver, open your console and [code]sudo apt-get install nvidia-glx-new[/quote]



:guitar:

---

### Post by BoomShaka on 2007-10-22
I have the same issue. Except my graphics gard is a different model.

When I try install envy it tells me
Error: Dependency is not satisfiable: xserver-xorg-dev

I have tried installing it via:
sudo apt-get install xserver-xorg-dev
but that returns:
E: Couldn't find package xserver-xorg-dev

Any suggestions?
Thx

---

### Post by JonnyBlazexx on 2007-10-28
I also have almost the completely exact problem.  I installed ubuntu 7.10 from the cd.  I downloaded the appropriate envy installer and find that a dependency is missing: "xserver-xorg-dev" and when i try the various commands that i have seen to try, I get the same error "E: Couldn't find package xserver-xorg-dev"

I am running a dell vostro 1500 with the 8400gs video card if that matters.  Right now im just using whatever drivers came with the Ubuntu install.  However I want to get the nvidia drivers working so that i can use their utility (which i like) to have multiple displays.

Thank you in advance!  

Jonathan

---

