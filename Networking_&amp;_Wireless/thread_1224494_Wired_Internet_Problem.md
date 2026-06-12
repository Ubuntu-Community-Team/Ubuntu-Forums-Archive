---
title: "Wired Internet Problem"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by sum1uhate on 2009-07-27
(I'm new to ubuntu, so not sure if this thread should go here or in the networking board)

I just installed ubuntu 8.04 as part of a dual boot system with windows XP SP3. However, I can't connect to the internet. I checked the network thing on the upper right corner of the screen, and the radio button next to one of the connections was checked. My system specs are in my signature.

I saw this fix somewhere else on the forums, which involved unplugging the computer, waiting fifteen seconds, and then rebooting. This works only if I go straight into ubuntu-if I go into windows, reboot, and then go back into ubuntu, I can't get back onto the internet.

I'm pretty clueless as to what to do. Internet works fine for Windows.

---

### Post by fbugnon on 2009-07-27
Are you using DHCP to connect your Windows installation?  If this is the case, Ubuntu should normally connect, unless there is a hardware detection problem.

---

### Post by hagg_k on 2009-07-27
Hi,
I'm new to Ubuntu/linux, but I had a similar problem with network connections etc.
I'm running Xubuntu (with LXDE interface-very nice) on a wubi install at the moment.

I fixed it by downloading [Wicd]("http://wicd.sourceforge.net/") from 
[http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)

Click on one of the mirrors and download the .deb file onto a thumb.

Log in to Ubuntu, and you should be able to open the .deb file from your thumb. It will tell you that 'it is better to install things with Synaptic' etc, but just click ok and install it w/o synaptic (since that needs a network connection obviously...)

I can't remember if I needed to reboot but it worked well for me.

Hope this helps!
Koos

---

### Post by Iowan on 2009-07-27
> **sum1uhate said:**
>  This works only if I go straight into ubuntu-if I go into windows, reboot, and then go back into ubuntu, I can't get back onto the internet. I remember an article (but don't remember where) and a couple of posts that mentioned problems when rebooting from Windows. Gist of the article was that driver's didn't always get reset without a full power-down.

---

