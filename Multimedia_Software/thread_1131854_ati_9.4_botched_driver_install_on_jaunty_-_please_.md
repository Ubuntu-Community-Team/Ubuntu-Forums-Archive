---
title: "ati 9.4 botched driver install on jaunty - please help!"
date: 2009-04-21
forum: Multimedia Software
---

### Post by robholt on 2009-04-21
Hi, I'm a bit of a noob, but have been using Ubuntu 8.10 for the last year or so and have managed with it until recently. I did an online upgrade of 8.10 to 9.04 after it was made known that the new ati 9.4 drivers would work with jaunty. I have one of the x1900 series ati readeons. Everything went fine with the upgrade until I tried to install the 9.4 drivers. On reboot, I get total screen garbage and lockup. I can get into the recovery window, but trying the reconfig video option doesn't work. It keeps warning me that I'm overwriting a custom video configuration and it won't do anything. I've tried to reinstall the drivers through the terminal, but it won't work telling me something about not having the right dependencies - have no clue what that means. Nothing works - including that command to reconfigure xserver-xorg. How do I at least get back to the original video configuration so I can get back to the desktop? I thought these drivers were suppose to work - what did I do wrong? thanks!

---

### Post by alex1973 on 2009-04-21
Your card is no longer supported by ATI's proprietary driver: [http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

Your only option is the open source radeon drivers.

---

### Post by robholt on 2009-04-21
Thanks Alex, so how can I switch back to the open source drivers in the recovery terminal? I didn't realize that video card had gotten so old....

---

### Post by _gpf_ on 2009-04-21
> **robholt said:**
> how can I switch back to the open source drivers in the recovery terminal?

The following terminal command should remove the proprietary ATI driver:

```
sudo sh /usr/share/fglrx/uninstall.sh
```

Reboot once you have done this.  At that point, you should be able to install the open source one via:

```
sudo apt-get install xserver-xorg-video-radeon
```

---

### Post by robholt on 2009-04-21
Thank you for that information!

---

