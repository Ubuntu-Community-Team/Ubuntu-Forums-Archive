---
title: "Ubuntu 12.04: graphical errors on return from Suspension"
date: 2012-06-02
forum: Multimedia Software
---

### Post by pooja on 2012-06-02
I've installed Ubuntu 12.04 from CD and I really prefer the GNOME desktop to Unity. However when I reactivate my HP Pavilion dv6000 laptop from Suspend Mode, after logging in, I've experienced consistent graphical errors to the point that I can no longer make out an icon from the other or restart the computer (see attached picture). I have an Nvidia GeForce 7400 graphic card so I installed the Recommended Additional Drivers of Nvidia. Can someone help me fix this problem, please?
Any input is well appreciated.

---

### Post by pooja on 2012-06-02
Hi,
I've solved this problem: just had to update Nvidia driver, turn off Additional Drivers, re-boot, turn new drivers on, reboot and voilà.
I first gave these 3 commands:
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```
Rebooted into GNOME, activated the "Additional Drivers (Recommended, updated version)", booted again and this time graphics were ok. Previously, Nvidia X Server showed I had version 295.40, now I have version 295.53. I immediately tried out by Suspending and Logging back in: no problem whatsoever.
So to anybody experiencing these problems, I suggest updating Nvidia drivers. Now and then, graphics under GNOME, are still a little slow to react, but much much better than the picture I posted earlier.

---

