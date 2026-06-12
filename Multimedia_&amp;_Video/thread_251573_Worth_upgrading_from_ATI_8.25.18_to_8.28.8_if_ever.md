---
title: "Worth upgrading from ATI 8.25.18 to 8.28.8 if everything works?"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by mobilehavoc on 2006-09-05
It seems this is becoming a common question for me...not sure if it's good or bad yet. :-D 

Everything works right now (XGL/Compiz, video, etc etc) with the Ubuntu distro 8.25.18 ATI driver. However, when I logout the screen remains black and I have read this has been resolved in newer ATI drivers. I've also read that the newer ATI drivers provide better OpenGL support and faster performance

However, I've also read nightmare stories on these forums of people trying to upgrade manually and totally killing their stable systems.

Can someone who upgraded from 8.25.18 (fully working) to 8.28.8 please post your opinion of whether it's worth the risk of farking up my Ubuntu install or if I should just wait until I suppose an ATI driver is updated in the repos.

Much appreciated.;)

FWIW, my setup:
Intel P4 630 (3.2ghz)
2GB of RAM
ATI X800XL 256MB PCIE

---

### Post by whatever on 2006-09-05
if you use lots of java swing applications you may want to update, as java's 2d opengl acceleration for swing (Dsun.java2d.opengl) finally works with the new driver.
otherwise you probably won't notice any difference. you will _not_ get better performance and chances that any of your problem is fixed with the new driver are very low.

if you are new to linux and did the driver install by copy&paste from some howto you should probably stay with the old driver.
but if you got some basic knowledge about kernel modules and xorg you might try the new version, as you should be able to revert to the old version easily in case any new problems occurs. however, you shouldn't expect any miracles from the new version.

---

### Post by mobilehavoc on 2006-09-05
> **whatever said:**
> if you use lots of java swing applications you may want to update, as java's 2d opengl acceleration for swing (Dsun.java2d.opengl) finally works with the new driver.
otherwise you probably won't notice any difference. you will _not_ get better performance and chances that any of your problem is fixed with the new driver are very low.

if you are new to linux and did the driver install by copy&paste from some howto you should probably stay with the old driver.
but if you got some basic knowledge about kernel modules and xorg you might try the new version, as you should be able to revert to the old version easily in case any new problems occurs. however, you shouldn't expect any miracles from the new version.
Thanks for the honest answer. Quick question though, am I to understand that if I don't uprade using the many How-Tos right now at some time in the future when there's a newer ATI FGLRX driver released in the Ubuntu repos, it could be installed using a regular apt-get upgrade or Synaptic?

What I'm asking is will I at some point have to do the driver upgrade manually or do I just have to wait for a new version to be in the repos and then it'll be automated?

---

### Post by whatever on 2006-09-05
> **mobilehavoc said:**
> if I don't uprade using the many How-Tos right now at some time in the future when there's a newer ATI FGLRX driver released in the Ubuntu repos, it could be installed using a regular apt-get upgrade or Synaptic?
_if_ there is a new version in the repos you will get it with apt-get upgrade. but as long as no critical bugs are discovered in the current version, it is quite unlikely that a new version of the driver will hit the repos. if you want new drivers via the ubuntu repos you will have to wait for the edgy release and do a dist-upgrade then...

---

### Post by mobilehavoc on 2006-09-05
Well I made the mistake of trying to upgrade and it failed miserably. 

Is there any How-To on rolling back to 8.25.18 (distro drivers)??

I just want to get it back to what it was. :( :(

---

### Post by mobilehavoc on 2006-09-05
Just when I was about to give-up...I found this guide and got 8.25.18 back and running perfectly.

[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue)

NEVER UPGRADING MY VIDEO DRIVER AGAIN!:-D [-(

---

