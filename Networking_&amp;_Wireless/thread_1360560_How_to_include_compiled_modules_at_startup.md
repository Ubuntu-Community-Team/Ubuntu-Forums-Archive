---
title: "How to include compiled modules at startup??"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by MrStill on 2009-12-21
My laptop has the Broadcom BCM4322 chip; I have downloaded and compiled the Linux driver from Broadcom. After running the make, I activated the driver as follows

```

sudo modprobe lib80211
sudo insmod wl.ko

``` 

This was by instructions included in the read me file. The driver works great. However, once I shutdown my computer I have to do this again at startup. Is there an easy way to have this done automatically at startup? 

Thanks

---

### Post by Zorael on 2009-12-21
Modules listed in **/etc/modules.conf** should be automatically loaded upon boot, so try adding them there, one per line. The file may be called just **modules** if you have an older release.

On a tangent, modprobe uses insmod, doesn't it? So wouldn't the following command work just as well?
```
$ sudo modprobe lib80211 wl.ko
```


edit: If it necessarily has to be run as a command, add it to **/etc/rc.local**, somewhere above the 'exit 0' line.

---

### Post by MrStill on 2009-12-21
Thanks for the reply.

I found the modules file as you mentioned. But, there were only module names with no paths; so, I am assuming there is a specific place this module should be stored. Does it matter if I store this module in my home folder and add a path to the module file or is there somewhere specific I should store this module?

Also, I am assuming that this module (after make) is kernel specific. Will I need to rebuild this module every time the kernel updates?

Thanks

---

### Post by smo0th on 2009-12-21
I don't remember the path where the drivers are stored but I also have a Broadcom wireless card and solved my issues with ```
sudo apt-get install b43-fwcutter
```

For loading modules, I agree with Zorael's advice, mine is that you should use the system's structure just to be on the safe side.

About you drivers path, take a look into ```
/lib/modules/$(uname -r)/kernel/drivers
```

cheers

---

### Post by Zorael on 2009-12-21
As far as I'm aware, modules should be placed in **/lib/modules/$(uname -r)**. That makes it **/lib/modules/2.6.31-16-generic** on my kernel.

Perhaps you need to run **depmod** after having placed them there to make modprobe work out their dependencies, not sure.

---

### Post by MrStill on 2009-12-21
Thanks to both of you. I put the driver and included files in this directory /lib/modules/<Kernel Name>/kernel/drivers/wifi.

I added the wl driver to the list mentioned above and I have wireless connection at startup. Now, I know for sure I will have to set this up at each kernel update. 

As for the workarounds and modules provided in Linux distributions, as of now none are compatible with BCM4322 chip set. The only viable options I found were this driver provided by Broadcom and NDISWrapper. My web searches provided this driver first, so I went with it.

For anyone reading this looking for a solution for this chip set on their computer. The driver and instructions are here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Thanks again guys!

---

