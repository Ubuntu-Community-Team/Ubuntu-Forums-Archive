---
title: "Nvidia legacy driver 7184 ?"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by Erwin123 on 2006-09-10
Hello,

the Nvidia legacy driver currently packaged with dapper (7174) has some issues with the "RenderAccel" option: the Xserver suddenly starts to run at 100% CPU and the keyboard is dead, the mouse may move, but you can't click anything... This bug is resolved in the new version of the driver which was released a few week ago. Without the RenderAccel option, the display is extremely slow (at least since some Xorg update and with my ancient GeForce2 card).

It would be very, very helpful if someone could package the latest driver from Nvidia and update "nvidia-glx-legacy" to version 1.0.7184.

Many thanks!
Erwin

P.S.: I started this thread probabely in the wrong forum ("Repository support") before. Sorry for opening it a second time, I don't know how to move the thread.

---

### Post by tseliot on 2006-09-10
If you can wait for few days I will provide some repos with the latest driver for Ubuntu Dapper.


If you can't wait you can try Envy

---

### Post by Erwin123 on 2006-09-10
Thanks a lot, that would be great! No matter if it takes some time.

Could you provide packages for "all" platforms? I have a 64bit kernel. (2.6.15-26-amd64-k8)

Cheers,
Erwin

---

### Post by tseliot on 2006-09-10
> **Erwin123 said:**
> Thanks a lot, that would be great! No matter if it takes some time.

Could you provide packages for "all" platforms? I have a 64bit kernel. (2.6.15-26-amd64-k8)

Cheers,
Erwin

sure. 64bit and 32bit

---

### Post by uboltun on 2006-09-18
> **Erwin123 said:**
> Hello,

the Nvidia legacy driver currently packaged with dapper (7174) has some issues with the "RenderAccel" option: the Xserver suddenly starts to run at 100% CPU and the keyboard is dead, the mouse may move, but you can't click anything... This bug is resolved in the new version of the driver which was released a few week ago. Without the RenderAccel option, the display is extremely slow (at least since some Xorg update and with my ancient GeForce2 card).

It would be very, very helpful if someone could package the latest driver from Nvidia and update "nvidia-glx-legacy" to version 1.0.7184.

Many thanks!
Erwin

P.S.: I started this thread probabely in the wrong forum ("Repository support") before. Sorry for opening it a second time, I don't know how to move the thread.


I have the same exact problem after installing 7184 driver. 
Firefox and Synaptics freeze until I turn off RenderAccel. 
I have GeForce2 Ultra.

---

### Post by Erwin123 on 2006-10-03
> **tseliot said:**
> sure. 64bit and 32bit
tseliot,
there are 7184 packages for edgy on 
[http://packages.ubuntulinux.org/edgy/misc/nvidia-glx-legacy](http://packages.ubuntulinux.org/edgy/misc/nvidia-glx-legacy)
but none for dapper. Are there issues with the dapper kernel 2.6.15, or would it be straightforward to compile the package for dapper?
Erwin

---

### Post by tseliot on 2006-10-03
> **Erwin123 said:**
> tseliot,
there are 7184 packages for edgy on 
[http://packages.ubuntulinux.org/edgy/misc/nvidia-glx-legacy](http://packages.ubuntulinux.org/edgy/misc/nvidia-glx-legacy)
but none for dapper. Are there issues with the dapper kernel 2.6.15, or would it be straightforward to compile the package for dapper?
Erwin

Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

and at the post on my website:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

You will find my repos for Dapper there.

---

