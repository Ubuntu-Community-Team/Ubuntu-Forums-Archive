---
title: "TabletPC HP Compaq TC1000 nvidia-glx-legacy?"
date: 2008-08-12
forum: Multimedia Software
---

### Post by mplexus on 2008-08-12
Hello.

Anyone that has succesfully installed proper nvidia glx drivers please
give me some advice! I'm trying to load glx nvidia drivers (GeForce2 Go) on tabletpc
HP / Compaq TC1000 (ubuntu 8.04.1). Note: the "nv" driver works fine, but I want to use the proprietary drivers.

**1.** should I install repository nvidia drivers and if yes should that be nvidia-glx-legacy?

**2.** _OR_ do I have to manually download and compile the drivers myself (NVIDIA-Linux-x86-1.0-xxxx-pkg1.run) - and if yes, what version?

I have already looked at this thread 
[http://ubuntuforums.org/showthread.php?t=200995&page=1](http://ubuntuforums.org/showthread.php?t=200995&page=1)
and tried kernel boot option irqpoll
and (added to /etc/modprobe.d/nvidia) NVreg_SoftEDIDs=0 NVreg_Mobile=1
with no success.

I post here my xorg.conf in case someone has the time to take a look and see if i made something wrong there.
[http://mplexus.no-ip.org/~mplexus/xorg.conf]("http://mplexus.no-ip.org/~mplexus/xorg.conf")

Note: the current situation when trying to start X with nvidia driver is that the screen goes black and no ctrl-alt-F1/F7/F8/backspace works.

Thanks in advace!

---

### Post by neospud1 on 2008-08-21
I'm bumping this because i have the same issue.  I have a tc1000 and can't get the video working right.  Its an nvidia geforce2 go video chip or card.  Mainly i want to get it working for the 2d performance while viewing web pages.  Its an awfully slow laptop.

---

### Post by charon79m on 2008-08-27
I'll toss in a "Me too!" on this.  I'm pretty well versed, but since 7.10 I've been striking out.

I've tried the binary drivers delivered by Ubuntu, most recent driver direct from NVidia, and magical versions for several sites splattered across the WWW.  

I'd love to hear of someone running 8.04 with good ol' 3d support and a working pointer.  I'd appreciate it even more if that person would be willing to share the magical sauce that made it all come together.

Mike

---

### Post by lukasfischer on 2008-12-21
i've got the same problems, anyone solved it yet?
thanks

---

### Post by mplexus on 2008-12-25
Well, according to this ( [http://www.razdva.cz/vencik/TC1000_And_Linux/](http://www.razdva.cz/vencik/TC1000_And_Linux/) ) one must manually compile nvidia version 1.0-7185 (available from the site above).

I did it and it fails on kernel 2.6.27-9. I must find an appropriate patch for the driver to be able to compile in this kernel.

If one tries this please post the results!

---

### Post by DesertEagle on 2010-01-17
yet another me too!

I've tried pretty much everything posted on the internet about how to get the nvidia drivers to work (including all the different kernel versions) as well as the nouveau drivers... but nothing yet.

---

