---
title: "XFX GeForce FX 5200 card driver ... ?"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by ebeyer on 2006-07-28
I recently put together a system with an Intel Celeron D microprocessor and an XFX GeForce FX 5200 (128 Mb) video card.

While Ubuntu is able to deliver me 1024 x 768 without trouble, I know I should be able to do better.  So I have two questions:

(1) Can I just add a higher resolution setting to my xinit.d file without blowing anything up?  Do I need to install the nVidia driver first?

(2) I've been poking around trying to find the right nVidia driver so I can do OpenGL and the like.  The closest thing I found is: [http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)

Do I want the IA32 version of the driver with my system or do I go with the FreeBSD version?

Any help for this linux newbie would be deeply appreciated.

EB

---

### Post by madmetal on 2006-07-28
first install nvidia drivers from synaptic.
open synaptic and search for nvidia driver.

---

### Post by tseliot on 2006-07-28
Try Method 1 of this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by ebeyer on 2006-07-28
> **tseliot said:**
> Try Method 1 of this guide of mine:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

I followed Method one, using the regular GLX driver and got no errors.  I rebooted the system and now I get an nVidia splash on loading the GNOME desktop.  I assume that means it worked?

I still can't get the resolution above 1024 x 768.  Do I just add "1280x800" to the resolutions settings in /etc/X11/xorg.conf, or will that mess something up?  Is there a better way to get some more resolution out of my card?

Thanks again.

EB

---

### Post by tseliot on 2006-07-28
> **ebeyer said:**
> I followed Method one, using the regular GLX driver and got no errors.  I rebooted the system and now I get an nVidia splash on loading the GNOME desktop.  I assume that means it worked?
Yep, it worked.

> **ebeyer said:**
> I still can't get the resolution above 1024 x 768.  Do I just add "1280x800" to the resolutions settings in /etc/X11/xorg.conf, or will that mess something up?  Is there a better way to get some more resolution out of my card?

In point 5 of the Problems Section of my guide you can find the answer to your question

---

### Post by ebeyer on 2006-07-28
> **tseliot said:**
> Yep, it worked.



In point 5 of the Problems Section of my guide you can find the answer to your question

I will try this when I get home and let you know how it goes. 

You must get tired of answering this question over and over.  Thanks.  Maybe this should be added to a Wiki someplace?

EB

---

### Post by ebeyer on 2006-07-28
> **tseliot said:**
> Yep, it worked.



In point 5 of the Problems Section of my guide you can find the answer to your question

I just wanted you to know that your tip worked like a CHARM!  Much joy today.

Thanks again.

EB

---

### Post by ebeyer on 2006-07-28
> **tseliot said:**
> Yep, it worked.



In point 5 of the Problems Section of my guide you can find the answer to your question

Monkeying around with the desktop, and now in KDE.  I'm finding the transparency settings aren't working.  Is this a function of the video card/driver or is this something I'm doing wrong in KDE?

---

### Post by tseliot on 2006-07-29
> **ebeyer said:**
> Monkeying around with the desktop, and now in KDE.  I'm finding the transparency settings aren't working.  Is this a function of the video card/driver or is this something I'm doing wrong in KDE?

transparencies in KDE work with or without 3d acceleration.

If you want to use the Nvidia driver you have to select Xrender acceleration instead of software rendering.

---

### Post by minhtrietle on 2007-07-21
thank you very much, tseliot !!!!!!!!!!!!!!!!!!!

envy program  helps a lot!!!!!!!!!!!!

beers to u

---

