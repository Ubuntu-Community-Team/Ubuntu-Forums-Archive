---
title: "Remove WLAN Driver"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by nixoninajar on 2013-03-08
Hello,

I need to uninstall my Wireless Lan Driver for  "Network controller [0280]:** Broadcom Corporation BCM43224** 802.11a/b/g/n [14e4:4353] (rev 01)".
It can't be simply blacklisted, it needs to be removed in a way that I can only reinstall it with the help of another computer. (i.e. removed completely) 
I don't have any 3rd party drivers installed, it's a clean Ubuntu 12.10 installation.

Thanks for any help!

---

### Post by chili555 on 2013-03-08
Is the driver not working properly? Are you certain that's the best way to fix it? Is the driver *wl*?```
sudo lshw -C network
```drver=??

---

### Post by nixoninajar on 2013-03-08
```
driver=brcmsmac
```

One of my students writes his finals on a laptop, he is not allowed to acess the internet, thus I need to properly uninstall the driver. (The WLAN card is not easily removable.)

---

### Post by chili555 on 2013-03-08
Would it not do just as well to blacklist the driver? The relevant directory, /etc is only writable by administrators and modprobe is only executable by admins. I assume you gave your student his or her own user account without having access to the admin password. Removing a driver built-in to the kernel is not as simple as sudo apt-get remove *driver*.

I would also find and blacklist the ethernet driver.

---

### Post by nixoninajar on 2013-03-08
Why the ethernet driver? The Exam takes place in a supervised room, and there is no ethernet. 

I successfully crippled the driver by deleting some "code" file and other files in a folder in /etc/drivers/. 
I searched for "brcmsmac" and found it this way, so I'm not sure where exactly it was. 
So issue solved, thanks [COLOR=#000000]chili555![/COLOR]

---

### Post by chili555 on 2013-03-08
Please post back if we can help you further. Please note that bcma depends on brcmsmac and probably needs to be temporarily crippled also. bcma carries the actual device ID aliases. I'm not exactly sure what you did but be sure to test carefully.

---

