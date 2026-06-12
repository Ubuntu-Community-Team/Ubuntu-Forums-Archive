---
title: "Linksys AE1000 Wireless USB Stopped Working on Reboot"
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by mark2741 on 2012-03-08
So I followed the directions on this webpage to get my Linksys AE1000 wireless USB dongle to work with Ubuntu:

[http://powerport.webs.com/linuxubuntu.htm](http://powerport.webs.com/linuxubuntu.htm)

It worked flawlessly! Perfect!

But...then I rebooted my PC and now it won't work. It does get recognized when I type 'lsusb' in the terminal:

Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [RaLink RT3572]

What can I do to make it work? I'm using the latest Ubuntu 64-bit, clean install.

---

### Post by chili555 on 2012-03-08
Please try this:```
sudo su
echo rt3572sta >> /etc/modules
modprobe rt3572sta
exit
```You will need to rebuild the module whenever a newer linux-image is installed by Update Manager. Any idea why the built-in rt2800usb didn't work? Firmware issue?

Post back if you need more help.

---

### Post by mark2741 on 2012-03-08
Thanks chili!

I think the problem was that, right after I got the wireless working, I then ran the ubunutu updater and that's why I rebooted. So likely the kernel was updated. So I just re-ran the install/make procedure and it's back up and working. I'll reboot to test but I'm confident it will work, and if not I saved the install instructions to a script file for future use : )

Thanks again!

---

### Post by chili555 on 2012-03-08
Glad it's working! Would you please use Thread Tools at the top to Mark Solved?

---

### Post by POWERPORT on 2012-10-13
Thank You using my site. The when original site went down. I remade the driver. I never knew so many people needed it.

---

