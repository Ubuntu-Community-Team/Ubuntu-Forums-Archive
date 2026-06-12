---
title: "Gutsy: Artifacts in video playback"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by digTro on 2007-10-17
I've noticed a problem in Gutsy while playing videos and while scrolling pictures. Some horizontal artifacts are appearing on screen. I didn't have this problem in Feisty. 

I use a nvidia 6800 GS graphics card. I'm using the binary nvidia driver from repos.  And I haven't enabled compiz-fusion. I'm running metacity only.

---

### Post by digTro on 2007-10-19
The problem is not specific to video playback alone. I tried Doom3 demo, even there I could see the horizontal lines when the picture on screen moves horizontally. 

When I upgraded,  the nvidia-glx driver was installed. I removed it and installed nvidia-glx-new.  Even with the new driver I have the same problem. I had a similar problem with XGL on Edgy Eft. I had uninstalled the xgl-server and the problem was solved. Can anything similar be done with Gutsy?

---

### Post by Frak on 2007-10-19
Have you tried [Envy Scripts]("http://albertomilone.com/nvidia_scripts1.html") instead?

---

### Post by digTro on 2007-10-19
> **Frak said:**
> Have you tried [Envy Scripts]("http://albertomilone.com/nvidia_scripts1.html") instead?

I thought the nvidia-glx-new driver is the same as the latest version available on the Nvidia site (v100.14.19). Does the driver in the repos differ from the official nvidia driver?

---

### Post by Frak on 2007-10-19
> **digTro said:**
> I thought the nvidia-glx-new driver is the same as the latest version available on the Nvidia site (v100.14.19). Does the driver in the repos differ from the official nvidia driver?
The nvidia driver from the Envy Scripts is custom compiled for your system. Other than that, not much different.

---

### Post by johnclevenger on 2007-10-22
I've a Geforce 8600 GT. I installed Envy and the horizontal artifacts persist. They're annoying enough for me to boot up Vista when I want to watch something longer than a few minutes.

---

