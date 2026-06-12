---
title: "EM64T card, poor performance, lack correct drivers"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by nalmeth on 2005-11-13
I just got a new computer, which is running a Gigabyte Intel EM64T processor with Hyperthreading Tech - BUILT INTO MOTHERBOARD.
Naturally I ignored all blasphemers expecting to see me running XP, and instead went ahead with previously proven BREEZY 5.10.
Obviously I had to install the AMD64 version, and must say I am not initially impressed with the lack of 64-bit support for a lot of applications (wine, flash, full java, etc), but am not discouraged. 
As I understand I need only create a 32-bit chroot environment until the time comes where support is available for 64-bit. Unfortunately I haven't gotten to this yet, because I am struggling with my graphics card.

My biggest disadvantage here is that I know next to nothing about hardware. I live in the virtual world, and let other people worry about the "real world".
Ubuntu offers upfront Nvidia and ATI Driver support, but my understanding of my graphics card limits my understanding of what it needs!
At first I thought it would just take care of itself (a nasty habit of a linux user) but practically no 3D application would function. 

-I first tried the NVIDIA Driver, but it made no difference at all, and wouldn't even show the NVIDIA logo that is supposed to appear. I then uninstalled that, and tried the ATI driver. Although when setting up this driver, it told me that the device was not found (:confused: ) it did in fact make a difference, and performs slightly better. Some 3D apps now work, but nowhere near as well as I think they should. Very skippy when they do happen to work (3ddesktop hasn't and still won't even launch!). 

?! My question after all this, is whether or not my graphics card is even supported, or whether I have made some error and it is after all a NVIDIA supported card - the manual that came with it didn't offer any inclination!

Am I making a blaring mistake here, or am I hooped?!

Take no mercy on me if its my fault, I would just like to know how to get my 3D apps going.

note: 
-I left the configuration file for NVIDIA intact after switching to ATI driver, is this a factor?
-If more info is needed I will supply
- Sorry for the long rambling post - feel free to email me

Thanks in advance!:KS 
nalmeth

---

### Post by Ptero-4 on 2006-06-05
In a terminal type this:
```
lspci > ~/pcibus.txt
```

And then post the contents of the file pcibus.txt which will appear in your home folder.

---

