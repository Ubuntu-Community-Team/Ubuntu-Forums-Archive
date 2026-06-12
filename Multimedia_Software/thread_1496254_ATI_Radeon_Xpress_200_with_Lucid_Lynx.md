---
title: "ATI Radeon Xpress 200 with Lucid Lynx"
date: 2010-05-29
forum: Multimedia Software
---

### Post by DaftPyramid on 2010-05-29
I'm running Ubuntu 10.04 on a PC with the integrated Radeon X200 card. 

Currently, I have the free Radeon drivers, but they're either awful or aren't working properly. I get some wonky graphics errors, and any 3D game crashes as soon as the 3D graphics are to be displayed. 

My card is no longer supported by fglrx. What can I do?

Any help would be greatly appreciated, thanks in advance.

---

### Post by dogafin on 2010-05-30
ive the same problem with the same card...... ati catalyst 10.5 just got released, so im gonna see what it can do for me. right now i just want compiz. ive seen posts where they purge fglrx drivers, the process was a bit too complicated for me, might be worth a try. im just waiting to come across a tut that isnt too vague that i could follow. but let me know what works out for you. it seems EVERYONE has been having this problem after 8.10

i know this is for karmic but read it anyway
[http://ubuntuforums.org/showthread.php?t=1436200&highlight=ati+lynx]("http://ubuntuforums.org/showthread.php?t=1436200&highlight=ati+lynx")
it might can explain alot for you.

---

### Post by DaftPyramid on 2010-05-30
Well, good luck with Catalyst 10.5, but that driver doesn't officially support the x200. When I tried it, I got the "Video Mode Not Supported" error.

Compiz and everything works fine for me, but there are just some weird graphical errors, and of course I can't play games. Even online flash games chug.

---

### Post by Mark Phelps on 2010-06-01
For future reference, the last ATI fglrx drivers that DID support your card came with Catalyst version 9.3 -- and that worked with Ubuntu versions prior to 9.04.

ATI has said several times that they will NOT be releasing new Lnix drivers for those cards.  So, there's no point in trying out any new driver versions.

---

### Post by DaftPyramid on 2010-06-02
So there's literally no way to get 3D support unless I go back to 8.10?

Compiz keeps crashing now, too.

---

### Post by DaftPyramid on 2010-06-05
Is it possible to use an older kernel along with Catalyst 9.3?

---

### Post by Pyronus on 2010-06-08
You could try the VERSA drivers. Compiz works fine for me I can play flash games and I can run World of Goo no problem. Of course if you do that you wont be able to suspend or hibernate. Its a complete cluster.

---

### Post by DaftPyramid on 2010-06-09
I'm getting Google results about cell phones and netbooks. This is a desktop.

---

### Post by boonenoob on 2010-06-10
yah, I have that card too. dont bother trying to install fglrx, it'll just break your opengl.
if you already broke opengl, my sig has a link to a post i made on how to fix it

---

### Post by Mark Phelps on 2010-06-10
> **DaftPyramid said:**
> So there's literally no way to get 3D support unless I go back to 8.10?

Compiz keeps crashing now, too.

I have one of the Legacy cards (x1650) and I get full effects in 10.04 with the open source drivers.  I'm surprised you don't.

As to 3D, you should get SOME acceleration with the open source drivers, just not as much as with the fglrx drivers.

The only two ways to "fix" this are:
1) Replace the current Xorg with an older one that Will support the fglrx drivers
2) Go back to using Ubuntu 8.10.

Neither is really a good solution, and both have their problems.

---

### Post by DaftPyramid on 2010-06-10
> **Mark Phelps said:**
> As to 3D, you should get SOME acceleration with the open source drivers, just not as much as with the fglrx drivers.


Well then I guess this thread is about fixing my problems with the open source drivers, because all 3D applications crash immediately for me.

---

### Post by Yellow Pasque on 2010-06-10
YOu can try the xorg-edgers ppa. It may help. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by DaftPyramid on 2010-06-13
> **Temüjin said:**
> YOu can try the xorg-edgers ppa. It may help. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Can you explain just what xorg-edgers is? Is it just an alternative driver?

---

### Post by Yellow Pasque on 2010-06-13
It's an updated driver (along with updates to other key packages in the linux graphics stack). In particular, you would get the r300 gallium3d driver, which is going to replace the r300 classic mesa driver: [http://www.phoronix.com/scan.php?page=article&item=ati_r300g_june&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r300g_june&num=1)

---

