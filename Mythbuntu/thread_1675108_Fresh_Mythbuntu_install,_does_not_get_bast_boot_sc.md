---
title: "Fresh Mythbuntu install, does not get bast boot screen"
date: 2011-01-25
forum: Mythbuntu
---

### Post by Dave M G on 2011-01-25
I have just downloaded and installed Mythbuntu 10.10 on a machine that had previously been running Mythbuntu for years. So I know the hardware can and should work in principle.

I needed a clean install because I had altered so many settings over the years that the machine had some odd configurations and broken features. Time for a fresh start.

It is an older machine, and it has some kind of Nvidia video card, though I'm not sure how to query it in order to find out which one, if this is important.

The install process went very smoothly. Not a single error or pause. It seemed to detect all hardware.

On first boot, it got to the purple screen with the white "Mythbuntu" text and the five dots that alternate between white and orange to indicate progress.

Then it stops. The dots are all white, and the screen does not change. I can wait forever and nothing changes.

If I press CTRL+ALT+DELETE I can reboot. When I reboot, if I choose one of the "safe mode" options in Grub, I can eventually get to a command prompt.

That, however, is all I have figured out to do at this point.

What else can I try to get it to work?

Thank you for any advice.

---

### Post by newlinux on 2011-01-25
hmm maybe take a look at /var/log/Xorg.0.log to see if X is having a problem booting.

lspci -v should give you some output that can help determing your video card. Does the liveCD work fine?

---

### Post by Dave M G on 2011-01-25
newlinux,

Sorry, you posted just before I could.

It turned out was the Nvida driver not being installed. During the installation, it said it did get installed, but I guess not.

I had to install it manually from the command line.

Thanks for having offered some help!

---

### Post by newlinux on 2011-01-25
No worries - driver loading was my first guess - glad you got it working.

---

