---
title: "Winfast PVR2000 under Ubuntu 10.10"
date: 2011-03-14
forum: Multimedia Software
---

### Post by ericbarch on 2011-03-14
I'm currently using a Leadtek Winfast PVR2000 capture card with a webcam connected via the composite port. I'm attempting to get the video working with a motion daemon.

I used to have the identical setup under Debian and everything worked out of the box. I'm now trying to get this working under Ubuntu 10.10 Server.

When I first boot up the PC, it works great. Randomly (anywhere between 1 and 10 days) I stop getting video. If I kill all motion instances and relaunch it, I'm only able to get a solid green output. I've tried killing off every motion instance again and used other command line apps that just end up giving me a solid black image.

After a reboot everything begins working again.

It's not a huge deal if the video feed dies once and a while, but is there any way to avoid rebooting the whole PC? Is there any way to figure out why the capture card can't be accessed after the video feed dies? Any help would be greatly appreciated. Thanks!

---

### Post by ericbarch on 2011-03-14
Just for future reference and anyone who needs a temporary fix...I've been able to get the capture device working again by unloading and loading the cx88_blackbird kernel module. This can be done by executing the following:

sudo modprobe -r cx88_blackbird
sudo modprobe cx88_blackbird

I'll keep playing around with this module and see if I can find a more permanent fix.

---

