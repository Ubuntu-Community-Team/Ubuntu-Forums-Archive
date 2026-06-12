---
title: "Wireless breaks due to kernel updates"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by Totenglocke on 2009-01-29
My wireless is not supported out of the box, but after downloading the madwifi drivers it works fine.  However, it stops working in either of the two kernel updates since 8.10 was released.  If I try using the same method of getting my wireless working with the updated kernels, nothing happens.  Any ideas?

---

### Post by diablo75 on 2009-01-29
Not sure what the exact cause might be.  Something similar happened with my brother yesterday.  He has a broadcom chipset.  After setting him up with windows drivers via ndiswrapper, that solved the problem... but we also had to reset the network ssid, encryption type and password.  Even though the device was behaving as if it knew what it was from before... it would never connect until after we basically recreated a new network for it to connect to (though part of this had to do with the fact that neither of us could remember his WPA2 password).

I think I'd shoot for using windows drivers and see if that does the trick.

---

### Post by trundlenut on 2009-01-29
I have a similar problem due to adding extra drivers for my card and the upgrade broke it, my problem is that I can't compile the driver from the source.

---

### Post by Racer-X on 2009-01-29
Check this posting out:

[http://ubuntuforums.org/showthread.php?t=1052932](http://ubuntuforums.org/showthread.php?t=1052932)

---

### Post by manuleka on 2009-01-29
quick reinstallation of driver might fix your problem, that worked for mine:
[http://ubuntuforums.org/showthread.php?t=1053583](http://ubuntuforums.org/showthread.php?t=1053583)

---

### Post by Totenglocke on 2009-01-30
Got it working.  Just go to the directory for your wireless drivers then:

sudo make clean
sudo make unload
sudo make install

then reboot and everything should work just fine.

---

