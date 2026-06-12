---
title: "Wireless in LiveCD, but NOT in installation"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by gaiterin on 2009-07-06
Hi!
I have a problem.

In ASUS x50r laptop, I have wireless conection in LiveCD mode, but when I install it:
 - I activate the driver for WIFI, but not works :(
 - The Wireless led is always off.

How can I fix it, please?
Maybe copy files from LiveCD to HD?

The problem is [this]("http://acurti.es/xca"), but nobody talks about it in LiveCD works.
Thanks very much!

---

### Post by t0mppa on 2009-07-06
LiveCD has a bit older files from when the CD image was created and a full installation updates all the files. Thus sometimes drivers work in one and not the other. However, you can't really stick with those older files forever, so it's better to just fix up your wireless driver to work with what you have.

Looks like the thread you posted had plenty of instructions on how to troubleshoot ath_pci driver issues for you card, did you try any of them?

---

### Post by diablo75 on 2009-07-06
What I'd do first is take your laptop to a router or someplace where you can get a hardline connection to the Internet via an Ethernet cable.  Then check for all available updates and install them.  Then restart.

I've had to do this with many laptops before and about 90% of the time applying new updates does the trick.

---

### Post by superprash2003 on 2009-07-06
ensure that your wifi switch is on , most cards have a ON/OFF switch

---

### Post by gaiterin on 2009-07-06
Hi! :)
It's working now :D
I must remove the private driver.
And do this: [http://acurti.es/Bca](http://acurti.es/Bca)
Resuming:
1.- Not install remove driver for wireless.
2.- Edit file /etc/rc.local (Alt+F2 and write gksu gedit /etc/rc.local).
    and write in the file: 
```
echo  1  >  /sys/devices/platform/asus-laptop/wlan
```
Just before:
```
exit 0
```

Thanks to all for the help :D
Cheers!

---

