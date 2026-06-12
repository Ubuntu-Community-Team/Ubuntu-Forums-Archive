---
title: "Recordmydesktop problem"
date: 2009-03-10
forum: Multimedia Software
---

### Post by steigerjb on 2009-03-10
Why is the quality of my recordmydesktop bad? (the black lines) The cube is coming apart, and the slow desktop effects. Thanks

---

### Post by steigerjb on 2009-03-10
bump

---

### Post by steigerjb on 2009-08-14
bump

---

### Post by steigerjb on 2009-11-07
went to advanced > performance > edited to attached screenshot

---

### Post by Crimm on 2010-05-13
I'm actually have the same issue and looking for a resolution.

PC specs:
Ubuntu 10.04
Nvidia 8800 GTS with Twinview enabled
Quad Core Extreme
8 GB of RAM

It works until I spin or flip the cube. When I do ... bad things happen :) glitching, etc.

I've also played with the settings. 

I have 3d windows enabled. I'm going to try without later today.

---

### Post by juanimela on 2010-05-17
Recording with 3d effects forces a lot of information to be written to the hard disk. No matter how much cpu and ram you have, it's the hard disk speed that counts. You can try a ram disk, so that the temporal files are written onto RAM, not the hard drive.

   To create a ram disk:


   mkdir /tmp/ramdisk; chmod 777 /tmp/ramdisk
mount -t tmpfs -o size=256M tmpfs /tmp/ramdisk/

  

And then you select /tmp/ramdisk as the work folder for 
gtk-recordmydesktop. You can also play with options such as "encode on the fly", frame rate and such.

---

