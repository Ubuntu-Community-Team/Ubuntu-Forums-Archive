---
title: "Just Upgraded to Edgy - Xserver cannot find screens"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by fatsheep on 2007-02-10
I just upgraded from Dapper to Edgy and when I restarted I get this big long error message about Xserver.  It said "No Screens Found" pretty prominently in it, I could copy the whole thing here if that's what's required but I think this error has to do with my use of the latest Nvidia drivers from the repository provided in one of the above stickies.  Has anyone else had this problem?

---

### Post by taurus on 2007-02-10
Boot into recovery mode and run

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

---

### Post by fatsheep on 2007-02-10
Tried that, unfortunately I get the same error.  Here is the important part of the message:

> 
Error: API mismatch: the Nvidia kernel module has version 1.0-8776, this X module has the version 1.0-9629.  Please make sure that the kernel module and all NVIDIA driver components have the same version.

[B]Fatal Server Error: 
No Screens Found[/B]


This is why I thought it was a conflict between whatever the Distribution update is trying to install and what the [Unofficial Nvidia Drivers repository](http://www.ubuntuforums.org/showthread.php?t=255929&highlight=fatsheep) had.  Synaptic also used to complained about my Nvidia drivers, saying it could not update them because it had to remove other software to do so.  Any ideas?

---

### Post by taurus on 2007-02-10
When you reconfigure your X, can you please try the **vesa** driver?

---

### Post by fatsheep on 2007-02-10
Excellent diagnosis - worked great.  Many thanks.

EDIT: However, when I try to reinstall the NVIDIA drivers I get the exact same Xserver error.  I'm using method one in this guide: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1).

---

### Post by taurus on 2007-02-10
What kind of video card do you have?

---

### Post by fatsheep on 2007-02-10
XFX Geforce 6600 GT (PCI-Express 16X)

---

### Post by taurus on 2007-02-10
I have XFX GeForce 6800XT and didn't have any problem with nVidia using that guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by fatsheep on 2007-02-10
I put that new edgy repository from that link into my sources.list file and did sudo apt-get upgrade && sudo apt-get update.  Had to install nvidia-glx and a few other packages individually because they were being held back but I got everything upgraded - restarted and the Xserver gives the exact same error.  :mad:

---

