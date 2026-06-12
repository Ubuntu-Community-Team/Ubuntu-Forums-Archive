---
title: "Linksys AE1000 Not starting on start up"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by baddnady23 on 2011-07-29
I recently purchased the Linksys AE1000 wireless USB network adapter.  After some struggles, I found and installed the Ralink_RT3572USB_drv2400 driver for it and it now works, however it won't turn on when I boot up the computer.  I have to manually unplug and then plug the adapter back in for it to work again.  Anyone have any ideas?  I followed the instructions on this how to for installing the driver.

[http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000]("http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000")

---

### Post by thefasterblueone on 2011-07-29
You could try adding this command to rc.local. 

```
ifconfig wlan0 up
```

To edit rc.local:

```
sudo gedit /etc/rc.local
```

Add it below this line:

_# By default this script does nothing._

Then make it runnable by all.

```
chmod a+x /etc/rc.local
```

---

### Post by baddnady23 on 2011-08-01
Worked like a charm, thanks

---

