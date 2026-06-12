---
title: "Anyone using the newly revised and updated openfwwf broadcom driver?  Thoughts?"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by kevdog on 2009-08-28
I'm running the older version of the broadcom openfwwf driver, but haven't updated to the newer release.  Anyone with any positive of negative experiences with this driver?

[http://www.ing.unibs.it/openfwwf/](http://www.ing.unibs.it/openfwwf/)

---

### Post by swoody on 2009-10-02
I *just* got the openfwwf firmware working on Ubuntu. I am using Karmic Beta, which works out great, as the firmware needs a kernel of 2.6.30.xxx or above. I used a how-to that someone wrote for the gNewSense community, but it works well for Ubuntu, too:
[http://leorockway.wordpress.com/2009/07/04/0c00-0-network-controller-broadcom-corporation-bcm4311-802-11bg-wlan-rev-01-take-two/](http://leorockway.wordpress.com/2009/07/04/0c00-0-network-controller-broadcom-corporation-bcm4311-802-11bg-wlan-rev-01-take-two/)
Please also note, that if you try this, you'll need to install 'build-essential' before you begin, and if you are running Karmic Beta as well, you can ignore the section about the new Linux image. After install, dmesg does confirm:
```
b43-phy0: Loading OpenSource firmware version 410.31754
```

---

### Post by kevdog on 2009-10-03
Are you sure the firmware needs kernel of 2.6.30.xxx or above?

---

### Post by swoody on 2009-10-04
I believe so. That's why the how-to has you download a different kernel to make it work. I tried before with an older kernel, and I was told that was the reason it didn't work at that time. Now running Karmic beta, and with a newer kernel, it works fine for me :)

---

### Post by kevdog on 2009-10-04
Let me double check that information -- I think I am using the 5.2 driver using Intrepid.  I'll have to check my kernel revision number but I think its lower than you suggest and I think the driver is loading.  Something is loading because I do have wifi.  Let me check a few things when I get home, but I believe the tutorial may be incorrect.

---

### Post by swoody on 2009-10-04
Well, again this is for gNewSense which is based off of Hardy Heron, if I'm not mistaken. So it may be an older version of the kernel that's required. Again, I'm not positive, but I'll look into it a bit further, too :)

---

