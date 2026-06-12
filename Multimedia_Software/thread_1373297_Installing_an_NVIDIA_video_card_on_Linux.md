---
title: "Installing an NVIDIA video card on Linux"
date: 2010-01-05
forum: Multimedia Software
---

### Post by c800957276 on 2010-01-05
Hi,
I'm trying to install Ubuntu (or Xubuntu) on a PC that has integrated on board video.  After that I want to disable the onboard video and use an NVIDIA GeForce 8400GS video card.
I tried it before, and got a lot of resolution problems.  This is what I did:
- First, I put the card in the PCI slot and modified the bios to use it as the default video, and booted from the ubuntu CD.  The installation did not go through as I got no screen output (I guess ubuntu did not recognize my video card).
- Second, I restarted and modified the BIOS so that the onboard video was the default.  This worked when I booted from the CD and installed, I got screen output and all.  I completed the installation and turned off the computer.
- Third, I installed the card on the PCI slot but did not change the BIOS, booted and used the onboard video, downloaded the NVIDIA driver (190.53) from the NVIDIA website, installed it, and turned off the PC.
- Fourth, I modified the BIOS so that the NVIDIA video was the default, plugged the monitor to the NVIDIA VGA output, restarted, and got ubuntu working at a very low resolution of 640*320.

This is where I am stuck.  I can't change the resolution to 1024*768 or 1366*768.  I only get 640*320.

Is there any way to avoid all this and do a fresh installation of ubuntu 9.10 with the NVIDIA card already in and as default on the BIOS?

I am thinking the resolution problems started because I got video drivers mixed up with intel onboard during installation, then NVIDIA.  I guess I should have removed the intel drivers first before installing NVIDIA drivers.  If anyone agrees, how do I uninstall Intel video drivers?

If that is not the case, how do I configure the NVIDIA drivers to work properly?

My PC is an older IBM 8303 KKU at 2.26GHz, with 2GB RAM, 40GB HDD, and a 512MB NVIDIA GeForce 8400 GS
Thanks.

---

### Post by huviduc on 2010-01-05
I would just install the system as usual, install envy, reboot, go into the BIOS, and disable on board graphics. Shut down and install PCI card. When you boot back up you will be left with a command line(if it asks you to configure anything, hit no). Login with user name and password. Run the following

```
sudo envyng -t
```

select "1" for Nvidia. Let Envy finish and reboot


P.S. Installing the basic system really doesnt take too long so if this doesnt work for some reason, you can always reinstall without wasting too much time.

---

### Post by realzippy on 2010-01-05
...meanwhile it would be *envyng -t*

---

### Post by huviduc on 2010-01-05
> **realzippy said:**
> ...meanwhile it would be *envyng -t*


Thanks for pointing that out. I will actually be doing this tomorrow night when my new card arrives so im glad you caught that

---

### Post by c800957276 on 2010-01-07
It did not work.  I tried a fresh installation but it did not work either.
Ubuntu works on my laptop.  I'm keeping it there, and going back to XP on this PC.
Thanks anyway

---

