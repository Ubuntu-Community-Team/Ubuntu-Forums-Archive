---
title: "Microphone capture stopped working"
date: 2010-11-29
forum: Multimedia Software
---

### Post by Grady Lemoine on 2010-11-29
Hi all,

I'm running Xubuntu 10.10 on an ASUS Eee 1215T; the sound hardware on the system is a Realtek ALC259, and there's also sound output through HDMI with an ATI RS690/780 HDMI chip (both according to alsamixer).  I was recently fiddling with the sound settings to try to get sound output through the HDMI port.  I was successful in that, but I can no longer record sound using the built-in microphone.  I'm pretty sure this is something I messed up, since sound recording worked correctly when I first installed Xubuntu, but I'm not sure what I need to do to fix it.  I've tried all the promising-looking settings in gnome-volume-control and xfce4-mixer to no avail, and alsamixer also shows everything, both playback and capture, at 100% volume and un-muted; alsamixer also shows that the capture is turned on.  I only used these tools (gnome-volume-control, xfce4-mixer, and alsamixer) to get the HDMI output working.  How do I find out what's wrong and fix it?

Thanks,

--Grady

---

### Post by tulku2 on 2010-11-29
Hi!

I know this will not answer your question, but I was thinking of buying this same netbook, Asus 1215T (amd based), but can't find any information online regarding as how good it works with Ubuntu.

I read that you are using Xubuntu. Did you have any problems with this computer? Video, WIFI, etc, apart from the recording issue you mention. Does it suspend correctly? What drivers are you using?

I would really appreciate this information! Thank you very much in advance,

Lucas

---

### Post by Grady Lemoine on 2010-11-29
It works fine for me; all the hardware seems to be correctly supported, though it does require a couple of proprietary drivers.  Don't try to use an earlier version of Ubuntu than 10.10, though; the wifi driver is proprietary, and since 10.04 and below don't ship with support for the wired network hardware, you'll have no network with the older versions.

Anyone out there -- help on the microphone thing?  I'm sure it's a software settings problem, but I don't know how to diagnose it.

--Grady

---

### Post by Grady Lemoine on 2010-11-29
Anyone?

---

### Post by nerdybrunette on 2010-11-30
I once had an issue using Lucid where I couldn't record as root. You might want to try that first as it would be the easiest solution.
 
I'm not sure what the Xubuntu layout looks like, but if you can access the "Sound Preferences" box, and go to the Input tab, if you tap on the microphone does the input level meter have any reaction? I'd try to mess with the settings on the Hardware tab of that dialog box, too.

---

### Post by lidex on 2010-12-02
> **Grady Lemoine said:**
> Anyone?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by rocatorreon on 2011-01-20
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6](http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6)

---

### Post by spoiled-tv on 2011-02-28
Has anyone made progress getting thier mic to work on a 1215t?

I am having the same issue

[http://www.alsa-project.org/db/?f=9365c997bb510d311cb815752535902f8d91f73f](http://www.alsa-project.org/db/?f=9365c997bb510d311cb815752535902f8d91f73f)

---

### Post by lidex on 2011-03-01
> **spoiled-tv said:**
> Has anyone made progress getting thier mic to work on a 1215t?

I am having the same issue

[http://www.alsa-project.org/db/?f=9365c997bb510d311cb815752535902f8d91f73f](http://www.alsa-project.org/db/?f=9365c997bb510d311cb815752535902f8d91f73f)

Did you update your alsa-driver-modules or do the alsa upgrade?

---

