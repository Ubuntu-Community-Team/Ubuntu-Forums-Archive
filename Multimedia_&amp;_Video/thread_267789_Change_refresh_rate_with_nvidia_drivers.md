---
title: "Change refresh rate with nvidia drivers"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by Linux_Maths on 2006-09-29
I have the following problem:
I need the nvidia drivers for games and openGL software, but when I install the drivers I can't set the screen resolution to 1024 x 768 at 75Hz. 1024 x 768 at 85Hz works, but it makes the screen blurry because my monitor is a bit old and doesn't work very good at higher refresh rates. 
I've already tried "sudo dpkg-reconfigure xserver-xorg" and manually edited the refresh rates in xorg.conf. All of this doesn't work.
Everything works when I use the 'nv' driver instead of 'nvidia' (except for openGL)
Does anyone know how I can set the refresh rate at 75Hz (now my only option is 85Hz)?

---

### Post by Linux_Maths on 2006-10-08
I found a solution [here]("http://www.ubuntuforums.org/showthread.php?t=185698&highlight=nvidia+resolution")

---

### Post by tseliot on 2006-10-08
> **Linux_Maths said:**
> I found a solution [here]("http://www.ubuntuforums.org/showthread.php?t=185698&highlight=nvidia+resolution")

If you have other doubts you can read the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

