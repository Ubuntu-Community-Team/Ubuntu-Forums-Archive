---
title: "Nvidia 8500 - Odd Problem"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Schwooter on 2008-03-05
I'm running Ubuntu Gutsy Gibbon 7.10, with a AMDx64 CPU with a gig of memory, Chaintech V4FN Ultra Motherboard, and a XFX brand NVIDIA GeForce 8500 GT. 

Recently, I've installed Ubuntu on my 160GB SATA drive. I've been trying to get my video card to work, and have been trying for some time. I've downloaded Envy, and that didn't work. So, I went to the Nvidia driver page, and downloaded the 169.12 driver. I installed it, and it seemed to work. 

Now, whenever I attempt to enable the restricted drivers, and reboot, I'm set into low-graphics mode. I select my monitor and drivers, and start up. The resolution ( which I set to 1024x768 ) stays in 800x600. So, I go to see if the restricted driver is enabled, and it isn't. In fact, I'm told it's "not in use." 

So, I repeat the process, and same results.

However, if I decide to just continue past the configuration in low-graphics mode, I just get a black screen.

I seem to be missing a simple step somewhere along the way. What am I doing wrong?

---

### Post by sanddgroper on 2008-03-06
Hi
You could have a look at the these files in the /var/log directory
dmesg
messages
syslog
To see if they shed any light on what might be the problem.
A blank screen could just mean your monitor can not handle
the signal.What monitor do you have.
Maybe we should look at the order people try to install the nvidia drivers.
Synaptic first
Envy second
And from nvidia last.

Cheers
Sandy

---

