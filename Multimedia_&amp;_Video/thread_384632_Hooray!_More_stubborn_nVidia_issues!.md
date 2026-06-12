---
title: "Hooray! More stubborn nVidia issues!"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by Super Ashura12 on 2007-03-14
Hello all you happy, video-card using people! I'm (surprise) having issues with a video card's installation. I'm running Edgy trying to install an nVidia GeForce Ti4200, however, after I install the nvidia-glx driver and nvidia-kernel-common and run "sudo nvidia-glx-config enable" AND change the Xorg "nv" to "nvidia"... it doesn't work, after the ubuntu loadin screen I get black... all black. After that I reboot into the recovery mode (as I can't even get a Console under the regular mode) and run "dpkg-xserver -pligh" (Note: I can't quite remember it...). Last time this happened, I had to do something to the effect of disabling the drivers for the onboard SiS760 chip, because they conflicted with each other, the only problem is that I didn't find the solution, a friend did, and he can't remember how he fixed it... Anyone got any ideas?

EDIT: Wow did I botch up the restoration method, here's what I did: "dpkg-reconfigure -phigh xserver-xorg"

---

### Post by al1b1 on 2007-03-15
[http://ubuntuforums.org/showthread.php?t=380790](http://ubuntuforums.org/showthread.php?t=380790)

---

### Post by Super Ashura12 on 2007-03-15
Thanks al1b1, unfortunately, it didn't work. It got closer, I actually got the whole X error message process, but no console afterwards. But I still had to restore it via recovery mode. Does Xorg keep an error log? Maybe if I could find it and post it, it could help a bit more ](*,)

---

### Post by mgmiller on 2007-04-01
> GeForce Ti4200, however, after I install the nvidia-glx driver and nvidia-kernel-common

I think you installed the wrong driver.  The GeForce  and GeForce2 chipset cards use the legacy driver.  You need to install the nvidia-glx-legacy package.  

First, uninstall the nvidia-glx and then install the legacy package, then change the driver from nv to nvidia and it should work.

---

### Post by Super Ashura12 on 2007-04-25
> **mgmiller said:**
> I think you installed the wrong driver.  The GeForce  and GeForce2 chipset cards use the legacy driver.  You need to install the nvidia-glx-legacy package.  

First, uninstall the nvidia-glx and then install the legacy package, then change the driver from nv to nvidia and it should work.

But this card is a GeForce 4, and is listed on the nvidia-glx list and not the nvidia-glx-legacy list :confused:

---

### Post by mgmiller on 2007-04-25
> But this card is a GeForce 4, and is listed on the nvidia-glx list and not the nvidia-glx-legacy list

You're right.  You should not be using the legacy driver.  I saw the ti designation of your card and thought it was an older card.  Geforce 4 cards should work with the regular driver.  I am sorry for the misinformation.

The command you used:
```
sudo nvidia-glx-config enable
```
 is no longer correct.  Someone in their infinite wisdom decided to change it for 6.10 and 7.04.  The right command is:
```
sudo nvidia-xconfig
```

This will set up the driver correctly in your xorg.conf.

Also, if you have a built in SIS video card, make sure it is disabled in your BIOS, if possible.  Then, as long as there are no mentions of it in xorg.conf, there shouldn't be any conflicts.

---

