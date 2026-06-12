---
title: "nvidia screen resolution"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by ninjaprawn on 2007-05-24
hi

i have a geforce 6200 with a tvout, and ive set the resolution of the tv to 1024x768 its set as a separate x server thru nvidia-settings with the restricted drivers for nvidia, so its all set up right!

its just that the quality of the tv at 1024x768 makes all writing unreadable! where as the moniter running at 1024x768 is fine! surely thats not right???

dont get me wrong, the quality of the video at full screen on the tv is somehow better than it used to be when i used windows! but it doesnt look quite right!

anyone have any advice???

also tho, less worrying is that i need to use TVOVERSCAN to move the tv image to the right about 1 inch and stretch the image vertically up and down, if posible!

anyone know where to put this in xorg.conf, and what values i would roughly need???

thanks! :)

---

### Post by ninjaprawn on 2007-05-25
ive just noticedthe auto update today had nvidia driver 9631 in it, so i up dated, rebooted and it made no difference!!!

---

### Post by ske1fr on 2007-05-25
When you say TV I assume you're connecting the output to a normal CRT television set.  An LCD television should give you a standard VGA socket.

If it's a CRT then bear in mind it's not going to give you the resolution of a computer monitor.  Broadcast TV is based on around 576 visible lines scanned horizontally back and forth, interlaced (imagine the odd numbered lines pasted first, then the even numbered lines filling in the gaps).  How are you going to get 1024 x 768 nice and sharp in 576 lines?  Yes, it's not really possible or we'd all be buying big TV sets instead of monitors!   800 x 600 pixels should look better, but your applications might be impossible, or difficult, to use.  As you've found, video is OK because it's actually lower resolution - I gather it's 720×576.  Now I've learned something - I understand why PAL DVD is 576!

Have a look at PAL in Wikipedia.  I can't help you with the Overscan thing, but I'm sure other people have struggled with TV out. 

Note to more knowledgable readers, I know this is a gross simplification.  Corrections welcome.

---

### Post by IcarusR on 2007-07-16
Check out this NVIDIA Accelerated Linux Driver Set README and Installation Guide, it has some info on TVOVERSCAN
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/index.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/index.html)

ske1fr I recon you are correct about TV resolution.

---

