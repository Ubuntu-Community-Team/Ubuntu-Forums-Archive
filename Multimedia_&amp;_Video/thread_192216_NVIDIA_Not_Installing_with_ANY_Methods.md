---
title: "NVIDIA Not Installing with ANY Methods"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by NickABusey on 2006-06-08
Hello everyone, I've read through all the WIKI Docs, Forum How-To's, and Guides that I could find, and followed them all to a T to install NVIDIA OpenGL support, but to no avail.

Here's my situation, I just installed 6.0.6 on a Compaq Presario R3140 US Laptop, with an AMD64 Processor, and nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3) for graphics.

I am currently using 'nv' and am in X successfully, everything works great. Except no OpenGL, no 3D. I've tried installing the drivers with Synaptic, no luck. I tried manually downloading the drivers from the NVIDIA site, following the wiki how-to, but the installer doesn't run. It says no linux kernel could be found to match the architecture or something similar, when I downloaded the proper AMD64 version. ](*,) 

I'd appreciate any help, thanks!

---

### Post by taurus on 2006-06-08
Have you tried
```

sudo apt-get install nvidia-glx

```

---

### Post by glotz on 2006-06-08
And after that make sure it's not nv but nvidia in /etc/X11/xorg.conf

---

### Post by NickABusey on 2006-06-08
I just did this. The first ran fine, and I edited the conf. When I run 'startx' it gives me "Module nvidia not found" and crashes out.

---

### Post by NickABusey on 2006-06-08
I just tried the method detailed [here]("http://www.nvnews.net/vbulletin/showpost.php?p=777569&postcount=5") still with no luck.

---

### Post by NickABusey on 2006-06-08
Anyone? I'd really love to get this working.

---

### Post by glotz on 2006-06-08
What kernel are you on then? ```
cat /proc/version
```

---

### Post by NickABusey on 2006-06-08
Linux version 2.6.15-23-amd64-k8 (buildd@yellow) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5))

Thanks

---

### Post by glotz on 2006-06-08
Ok, now as per advice #6 in [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) do you have installed linux-restricted-modules-amd64-k8? (Goto synaptic and search for that. You'll see if it's installed or not.)

---

### Post by NickABusey on 2006-06-08
Indeed I already had it installed. I re-installed it, and followed the directions. After removing an incorrect "Device:" entry the config script had added to my .conf file, I was back into X with OpenGL support! Thanks!

Unfortunately, I still only have on 800x600 resolution, but after modifiying my .conf file using the sample found [here]("http://forums.gentoo.org/viewtopic-p-1210105.html?sid=93048da92bc5559ffe51a4b9052b848e#1210105"), it works fully now.

---

### Post by glotz on 2006-06-08
:)

---

### Post by tseliot on 2006-06-09
[QUOTE=NickABusey]I just tried the method detailed [here]("http://www.nvnews.net/vbulletin/showpost.php?p=777569&postcount=5") still with no luck.[/QUOTE]
Try with this:
```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=[COLOR="Red"]4[/COLOR]
```

---

