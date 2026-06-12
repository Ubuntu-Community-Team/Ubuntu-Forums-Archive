---
title: "webcam doesn't work in virtualbox guest"
date: 2011-05-14
forum: Multimedia Software
---

### Post by DanBender on 2011-05-14
I'm trying to use Skype on my tv-computer, which is running Mythbuntu 10.10.

The Linux Skype client gives me horrible sound echo problems, and the Windows one is "garbage" when using Wine, so I'm limited to either dual-booting Windows (which is inconvenient) or virtualizing it.

So I'm trying Windows XP via virtualbox. I've installed the webcam drivers (Logitech C500) and the Skype client, and set up the VM where it recognizes the camera; however, when I try to start video capture in Skype (Skype options->video options) it gives me the error "Can't start video. Try closing other programs which might be using the webcam" or somesuch. The Logitech webcam software likewise can't access the webcam either, just black screen. The activity light on the camera is off, so no programs are accessing it.

The worst part about it is during the webcam drivers install, there's a webcam test screen - and it works! But then you have to reboot the computer (restart the vm) and after that it no work no more.

The camera works fine in the Ubuntu host using Cheese. It also works fine in the real Windows installation.

Has anyone had an error like this? I imagine it's a settings thing in Virtualbox rather than something else, but I'm not sure how I'd remedy it. I've got a post on the virtualbox forums as well, but most of the stuff I get when I search for "webcam" there is about issues where the guest can't see the camera at all (mine knows it's there).

I'm willing to try other virtualization systems as well, if someone thinks a different one is likely to produce better results.

Thanks in advance,
Dan

---

### Post by no2498 on 2011-05-15
you may try stetting the echo to off in the adobe settings manager

---

### Post by DanBender on 2011-05-16
In the host? Or the guest? There shouldn't be any adobe anything in the Windows guest right now. If it's the Ubuntu host, I don't have any menu items with that or similar names (mythbuntu has a much more limited "applications" menu, not "applications, places, system").

---

