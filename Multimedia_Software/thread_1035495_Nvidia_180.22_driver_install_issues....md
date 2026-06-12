---
title: "Nvidia 180.22 driver install issues..."
date: 2009-01-09
forum: Multimedia Software
---

### Post by rayj on 2009-01-09
Hello, all. I'm certain that there are a few posts here regarding similar issues, but I haven't found anything specific to my problem.

I have an Nvidia 8800GT card in my Ubuntu Studio 64-bit install. When I first installed it, I had a host of similar issues getting the Nvidia 177 driver to run. Eventually, I managed to get it up and running on an older version of the 2.6 realtime kernel (I cannot remember the whole number...the version ending with 22, as opposed to the newer 23 and up...). This worked just fine, so I used it for quite some time.

This morning I decided to use the new 'stable' Nvidia driver (180.22). After flapping around a bit (I'm definitely a newbie-ish linux user), I figured out how to use Nvidia's installer to install the driver. The installer application stated that the driver was successfully installed.

Unfortunately, what I now have is a display limited to 640X480 max, a new Nvidia system tools applet, and a restricted device manager that maintains there are no restricted drivers in use (the Nvidia driver isn't even on the manager's list).

Edit-I just remembered that the proprietary Nvidia driver isn't part of the restricted device management system, therefore it wouldn't be listed there...right? Excuse me on that one...

I've poked around in xorg.conf, but I don't really know what I'm looking for. Does anyone have any suggestions as to where to start? I'm a bit lost...

Thanks for your attention.

Later edit:

Problem solved. Bouncing back and forth between kernels had Nvidia's application kicking out a new xorg.conf every time I used it, and it was modeling itself off of the low-res default setting. I simply looked through all the files, found the one that listed a reasonable range of settings, and copied it to /etc/X11/...

Note: the new drivers work very well indeed.

---

