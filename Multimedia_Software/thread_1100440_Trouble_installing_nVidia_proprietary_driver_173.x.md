---
title: "Trouble installing nVidia proprietary driver 173.x.x.x"
date: 2009-03-19
forum: Multimedia Software
---

### Post by mulluysavage on 2009-03-19
I just re-installed the nVidia proproetary drivers for my geForce 8300 chipset, to get sound working again - it stopped after a gStreamer updated. Now the video driver is not working. I installed driver 173.x.x.x, which was working before, and the installer said it was already installed.

Now when I boot up, I get a running in low-graphics mode dialog, and it says my driver is not running. I do select geforce 8 series from 'manually select driver,' but still get no options past 800X600. Also, there is no option for my monitor model.

I am getting the dreaded "apparently you are not using the nVidia X driver, please edit your X configuration," but runnin nvidia-xconfig as root successfully results in no changes.

What to do next?

Mythbuntu 8.04
Asus M3N78 Pro w/ geforce 8300
Acer X183H 1366x720

---

### Post by klemes on 2009-03-19
did you tried a reboot just after running nvidia-xconfig?

---

### Post by Pixtu on 2009-03-19
I have exactly the same problem, albeit with a different nVidia chipset (GeForce Go 6400).

And yes, I tried a restart straight after running nvidia-xconfig and still have the same problem.

The system can only start in 'low graphics' mode.

I think the driver must be there somewhere but it can't be found on start up.

I'm hoping that it just needs a simple change to a config file but don't know which one.

---

### Post by norwoods on 2009-03-19
nvidia has lots of help in their README files for drivers.

browse to:
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

click on Current official release: 173.14.18(x86

scroll down to: Instructions for those wishing to edit their X config file by hand can also be found in the README.

click on README

---

### Post by Pixtu on 2009-03-19
Thanks, but have tried this already.

Couldn't see anything in the README that tells me what's going wrong.

I'm just going round in circles. Everything comes back to the hardware not being recognised at start up and ending up with low res graphics mode. I then have to use xfix via the recovery boot option.

---

