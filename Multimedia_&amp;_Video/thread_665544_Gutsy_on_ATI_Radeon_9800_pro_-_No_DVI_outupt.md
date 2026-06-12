---
title: "Gutsy on ATI Radeon 9800 pro - No DVI outupt"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by fabecool on 2008-01-12
Hi folks, 

First of all, I did read lots of posts, but maybe not THE ONE that would help me, so if you think you've got something for me, it'll be very welcome!

I am kind of new to Ubuntu and Linux in general, although I have posted before. I had tried to have my Nvidia card give me some 1280*1024, but it never worked and I just gave up and went back to winXP hoping that some future version of Ubuntu would solve the problem. ([http://ubuntuforums.org/showthread.php?t=306157](http://ubuntuforums.org/showthread.php?t=306157)) 

I just got a second hand ATI Radeon 9800 pro, and since gutsy has just been released, I thought I could at last get rid of winXP and move to Ubuntu. I am not a gamer, but I use my computer for email, office work, watching movies and playing videos and music. 

One important thing though is that I should have the image coming to my monitor's DVI connector, since it gives a much higher quality image than the VGA. But in this case, it is not even possible to have the image at all on the DVI. The funny thing is that only my DVI was connected when I ran the live CD and installed ubuntu, and I got a great image, so I really wonder why it does not work anymore. Once I finished the installation, I rebooted, got the CD out of the drive and restarted... and then nothing.

I waited, but I only got a black screen and my monitor went onto sleep mode.

I have read a lot of posts and howtos on this forum and other websites, but none help. 

The first funny thing is this: when I first tried ubuntu, if I typed > sudo gedit /etc/x11/xorg.conf I would get the content of my xorg file. Now I only get an empty document. If I browse to the xorg.conf location, then I can open it and see its content, but I cannot update it.

Then at some point, Ubuntu notified me that some restricted drivers should be installed, so I clicked and it opened the restricted drivers manager for me. I checked the Ati accelerated graphic drivers, and  accepted; but I got the error message "could not apply, fix broken package first".  What is that? What does that mean?

I looked at the synaptic package manager where I thought I should install the fglrx driver; but it won't let me. I get the following error message:
> fglrx-control:
 Depends: xorg-driver-fglrx but it is not going to be installed
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable


Any help on that? I have no idea what that means. 

I also tried the "update manager", in case it would go fetch something and install it for me, but hey, I know I should not dream too much. And indeed, no miracle happened...

Anyway, overall, my impression on Ubuntu is very positive (even better than last time when I tried the previous version) and I would hate to have to go back to winXP (let alone vista, my machine could probably not handle it anyway...). 

Actually, I have not tried my old NVidia card (FX5200) with this 7.10. Do you think I could get the DVI working on this release, if there was no way I would get it in the previous (apparently because of the crappy chip of the graphic processor, so not really related to Ubuntu, although it works just fine in Windows).

Thanks in advance for any help, or even for clarifying what those error messages mean

---

