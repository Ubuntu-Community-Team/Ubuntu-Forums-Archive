---
title: "Video Caputure, Editing &amp; Converting in Linux"
date: 2010-01-20
forum: Multimedia Software
---

### Post by dodle on 2010-01-20
I have been wanting to make Ubuntu my main OS for a while now, but I do a lot of video work and some of the software I use is proprietary and made for Windows.  

I have slowly been trying to switch completely to freeware and open source software.  I figure that If I can do this, then I can most likely do all of my video work on Linux.  

Here are my main concerns:

What DV video capture utilities are available for Linux?  

What tools are available for encoding to MPEG-2?  I use Avidemux a lot for joining and separating video segments, but I do not like its MPEG encoders.  lavc pixelates the first few frames, and the last time I tried mpeg2enc it wasn't working at all.

---

### Post by sports.car.guy on 2010-01-20
> **dodle said:**
> I have been wanting to make Ubuntu my main OS for a while now, but I do a lot of video work and some of the software I use is proprietary and made for Windows.  

I have slowly been trying to switch completely to freeware and open source software.  I figure that If I can do this, then I can most likely do all of my video work on Linux.  

Here are my main concerns:

What DV video capture utilities are available for Linux?  

What tools are available for encoding to MPEG-2?  I use Avidemux a lot for joining and separating video segments, but I do not like its MPEG encoders.  lavc pixelates the first few frames, and the last time I tried mpeg2enc it wasn't working at all.

One of the most powerful and flexible pieces of software I found for all out video editing, simple conversions, whatever has to be Kdenlive.

Check it out, you might like it. :D

---

### Post by dodle on 2010-01-20
Thanks, I will check it out.  I've heard of it, may have even installed it at one point, but never used it.

---

### Post by sports.car.guy on 2010-01-20
> **dodle said:**
> Thanks, I will check it out.  I've heard of it, may have even installed it at one point, but never used it.

I would grab it from the actual website, not repositories. The one on the repositories is usually crippled and also it isn't usually one of the newer builds.

---

### Post by dodle on 2010-01-21
[http://www.kdenlive.org/](http://www.kdenlive.org/) recommends adding an alternative repository to synaptic:

[quote=kdenlive.org]Ubuntu Karmic 9.10

Kdenlive 0.7.5 packages are available at [http://packages.ubuntu.com/karmic/kdenlive](http://packages.ubuntu.com/karmic/kdenlive). OLD RELEASE, NO SUPPORT PROVIDED!
This version of Kdenlive is deprecated. It is strongly recommended to install Kdenlive 0.7.6 packages using sunab alternative repositories:

   1. go to System Menu > Software Sources > Third-Party Software;
   2. click add and paste this line in:
      ppa:sunab/ppa
   3. close software source and click reload.

In karmic the ppa keys are retrieved automaticaly

Then click the reload button of synaptic and install Kdenlive package or type the following command line :
sudo apt-get update && sudo apt-get install kdenlive[/quote]
Should I do that rather than just download the .deb?

---

### Post by sports.car.guy on 2010-01-21
> **dodle said:**
> [http://www.kdenlive.org/](http://www.kdenlive.org/) recommends adding an alternative repository to synaptic:


Should I do that rather than just download the .deb?

You definitely should. That way each time they release a new version you are able to update very easily, like when you normally update your system. They are constantly updating it, fixes, adds, etc, so it is nice to have it say hey I got a new version for you.

---

### Post by dodle on 2010-01-21
Cool, thanks.

---

