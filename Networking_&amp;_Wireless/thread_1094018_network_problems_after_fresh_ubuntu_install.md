---
title: "network problems after fresh ubuntu install"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by beun on 2009-03-12
I havent got alot of experience with linux but allways been able to fix the little problems i came across untill now.

After i installed a fresh version of ubuntu on my pc next to windowsxp with duelboot my wired network is no longer working in windows. It just says no cable connected. The weird thing is that it is working in ubuntu just fine.

I've tried to reinstall my network drivers but no luck so far, my wireless connection is working on both systems though.

Anyone that could help me with this issue?

Thanks alot

beun

---

### Post by xpod on 2009-03-12
You could always try and uninstall the network card from the XP device manager then reboot to reinstall it.That`s probably the best thing to try.

Did you resize the XP partition/drive to make room for Ubuntu and if "yes" did you give the Windows install a good defragging before you shrunk it?
Failure to do so can cause problems with Windows but you probably wouldn`t be able to boot into XP at all if that *was* the case.

---

### Post by beun on 2009-03-12
thanks for the reply,

And yes have tried that, didnt do anything. And i havent touched the windows patition at all. 

Found some new drivers for my network card today so going to give that a shot.

---

### Post by beun on 2009-03-13
no luck so far, new drivers didnt help.

anyone got an idea of things i could try?

thanks

beun

---

### Post by xpod on 2009-03-13
> anyone got an idea of things i could try?

Wine?
XP virtual machine within your Ubuntu install possibly?
Finding alternatives to your Windows app`s mabey.:D

Or try another network card with XP as that will at least narrow things down somewhat.Strange that it works in Ubuntu but not Windows though.
Especially if it`s not just a cable that was loose at the time or some messed up settings of some sort....

---

### Post by beun on 2009-03-14
> **xpod said:**
> Wine?
XP virtual machine within your Ubuntu install possibly?
Finding alternatives to your Windows app`s mabey.:D


messed about a bit with virtualbox and wine, got all the apps i need running on linux now. pretty cool. 

Only got a low fps while gaming on linux but meh will do for now.

thanks xpod

---

