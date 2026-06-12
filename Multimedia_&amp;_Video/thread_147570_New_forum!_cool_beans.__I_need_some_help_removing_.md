---
title: "New forum! cool beans.  I need some help removing kernels."
date: 2006-03-20
forum: Multimedia &amp; Video
---

### Post by glassgloss on 2006-03-20
Hey guys, 

I followed all of the directions over at the wiki to enable the lowest latency audio interfacing possible.  This lead to a bunch of problems for my Thinkpad t22.  mainly wireless and usb, although also some sound card and video card uncompatability problems.  Anyway, I went through uninstalling the kernels as guided by the wiki and everything went fine exept: 
sudo apt-get remove nvidia-kernel-2.6.12-50preempt
now.  I am not sure which version I have, so that would probably help to find out.  I am sure there is a way to tell, I just don't know.

I am hoping this resolves my last issue of a game lagging about every 4 seconds and being altogether unplayable.  However, I am not sure if it will because my laptop seems to be performing a bit under the weather since I have tried all this.  So what I am saying is I am not sure if this is a problem of my video card compatability having originated from installing the kernel or if it is just a problem of my laptop cpu and memory being pushed too hard for some unaparent reason?

I am not giving up on the ubuntu studio project!  I am still behind the revolution all the way, but due to compatability problems, I will be waiting for mubuntu! (maybe?)

Thanks for any help

---

### Post by dolson on 2006-03-20
Firstly, Dapper is much improved over Breezy for this, and even includes basic pre-emption in the default kernel. It should be a better distro until Mubuntu (if that's what it'll be called) is released.

Now, onto your issue, I have no idea what your 4-second lagging thing is about because if you removed the kernel you compiled as the tutorial said to, then you should have rebooted since then. If you did, then you are not running the custom kernel, and therefore not using the custom NVIDIA driver package. So your issue would not be caused by the wiki tutorials.

You didn't post your error message that you got when trying to remove the NVIDIA module.

To find out your currently running kernel version, type in uname -a.

To check what packages you have installed, type in dpkg --get-selections, or browse through them in Synaptic.

---

### Post by glassgloss on 2006-03-20
E: Couldn't find package nvidia-kernel-2.6.12-50preempt


I have tried going back through the archives with it and plugging in older versions, but I cannot find what it is I installed.  I browsed through the packages I have installed and couldn't find anything with nvidia in it exept for nvidia-kernel-common which leads me to believe I don't have any nvidia packages installed?

All I can say is that the lag was not there before the kernel swapping, and now it is.  I don't mean to blame the wiki for it, I am just trying to troubleshoot it out.

I may be a bit behind, is Dapper released?  Is Dapper a division of ubuntu like kubuntu or is Dapper a... version of ubuntu like breezy badger.  How do I update and do I need to backup all of my files first?

---

### Post by dolson on 2006-03-21
That step in the wiki is only for people who built and installed the NVIDIA modules. You don't need to type it if you didn't install the modules, because they won't be there.

Dapper is in development. But you can still run it. Although it's not recommended.

---

### Post by gosh on 2006-03-22
[quote=glassgloss]
I may be a bit behind, is Dapper released? Is Dapper a division of ubuntu like kubuntu or is Dapper a... version of ubuntu like breezy badger. How do I update and do I need to backup all of my files first?[/quote]

Dapper Drake is the next version, the successor of Breezy Bagder. It will be released in june. You can download the test version of Dapper Drake, Flight 5 here [http://www.ubuntu.com/testing/flight5](http://www.ubuntu.com/testing/flight5). This is a test version, so you might run into the occassional bug, but I run it without any hassle.

---

