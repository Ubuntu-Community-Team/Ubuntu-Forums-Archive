---
title: "Poor display resolution with Ubuntu 12.10 and AMD Radeon 9200"
date: 2013-04-01
forum: Multimedia Software
---

### Post by fatview on 2013-04-01
Hi, I am a brand new Ubuntu user so please be patient with me. I've been struggling with this all weekend and I've searched the forums, with no success.

Installed Ubuntu 12.10 on my old Sony Vaio.
I have a Samsung SyncMaster 206BW display which is supposed to provide max resolution of 1680X1050, but I am only getting 1280x1024 resolution.
I am pretty sure this is a driver issue. I have tried the following:

sudo lshw -c video

which results in:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: RV280 [Radeon 9200]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:e0000000-efffffff ioport:8800(size=256) memory:fe8f0000-fe8fffff memory:fe8c0000-fe8dffff

Looks like there is no driver installed. System settings indicates I am using the VESA: V280 driver.

After searching forums I did try using the proprietary driver fglrx. However when I did that, I got a blank screen and the only thing I could do was open a terminal, and purge fglrx, which brought me back to where I started. I am getting conflicting messages from the forums, but some posts claim that Ubuntu 12.10 doesn't support AMD/ATI drivers. Do I need to use the open source "radeon" driver?

Any help would be greatly appreciated, especially step-by-step instructions since I am still getting the hang of this. Thanks in advance!

---

### Post by carl4926 on 2013-04-01
I don't think you can do any better than that with that old hardware
Mostly because ATI dropped the ball

---

### Post by fatview on 2013-04-01
Thanks for the reply carl4926. This is discouraging though. It is an old machine that I wasn't using, which is why I chose it for my first Ubuntu installation as an experiment. I don't really want to invest a lot of money in new hardware.

---

### Post by carl4926 on 2013-04-01
> **fatview said:**
> Thanks for the reply carl4926. This is discouraging though. It is an old machine that I wasn't using, which is why I chose it for my first Ubuntu installation as an experiment. I don't really want to invest a lot of money in new hardware.

If I could just beg you to be patient for additional feedback.
Others may have advanced knowledge.

---

### Post by Yellow Pasque on 2013-04-01
fglrx/Catalyst is not the solution here and it hasn't supported R200 based cards in a loooooong time (2006). That has nothing to do with ATI/AMD "dropping the ball", since the open-source driver quickly became better in a lot of ways (especially for those of us who actually remember fglrx 8.28.8). Anyway......

> Do I need to use the open source "radeon" driver?
Yes, and it should work out of the box.
Post your /var/log/Xorg.0.log

---

### Post by fatview on 2013-04-01
Thanks Temujin. Here is my /var/log/Xorg.0.log. This is a long file, sorry to paste it in like this! What are we looking for in this file?

   
**Edit by sandyd: removed log - please paste to pastebin/paste.ubuntu.com - thanks**

---

### Post by carl4926 on 2013-04-01
OK
That's crazy. You should use
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Hopefully a Mod will edit that out and transfer it

---

### Post by fatview on 2013-04-01
Sorry Carl. I used the link you provided. I think the file should be here:

[http://paste.ubuntu.com/5667594/](http://paste.ubuntu.com/5667594/)

---

### Post by Yellow Pasque on 2013-04-01
> [KMS] drm report modesetting isn't supported.
Try a newer graphics stack: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by fatview on 2013-04-02
Thanks Temujin. I tried the graphics stack you suggested but it created a new problem-- I am now only getting a wallpaper background with no dash. My exact steps so far:

sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get dist-upgradeRebooted and I just had the wallpaper, nothing else. I also received an error message that Compiz isn't working. I was able to open a terminal (Ctrl-Alt-t) and I started following instructions given here:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Unity is installed, ubuntu-desktop is installed, compiz is installed. I ran software-properties-gtk and checked Additional Drivers, it says no proprietary drivers are installed. I then tried:

/usr/lib/nux/unity_support_test -p

And got "no" answers for "Not software rendered" and "Unity 3D supported", yes answers for everything else.

I am doing my best to troubleshoot this on my own but I am getting to a point where I feel like I am getting lost, so I thought I should check in with the forum again. Any ideas on what I should do next?

Thanks very much!

---

