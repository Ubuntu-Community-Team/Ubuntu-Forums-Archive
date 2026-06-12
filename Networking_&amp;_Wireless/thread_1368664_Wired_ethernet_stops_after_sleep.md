---
title: "Wired ethernet stops after sleep"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by GmAz on 2009-12-30
For some reason my wired connected won't come back on if I put my netbook to sleep and wake it back up.  My wifi works fine, but my Atheros 9285 chipset doesn't talk well with my Linksys N router.  I get a connected, but it usually sits at around 10 kb/s and that is just annoying as hell.  

Anywho, why is my wired eth0 connected failing to reinitialize when i bring my netbook back from sleep?  how can i start up the connection manually without having to reboot?  

And yes, I've unplugged the cable and back in, but its more like the port itself is gone.  I run ifconfig and it doesn't show a physical port.

---

### Post by shredder12 on 2009-12-30
you can try to restart the connection using this command
```
sudo /etc/init.d/networking restart
```

The interface should be visible by using "ifconfig", if not try 
```
ifconfig -a
```

Once you have indetified the interface you can deactivate and reactivate it using 
```
sudo ifconfig eth0 down
```
```
sudo ifconfig eth0 up
```
replace eth0 with your interface..

---

### Post by GmAz on 2009-12-30
sudo /etc/init.d/networking restart and ifconfig -a both didn't work.  the wired connection didn't start back up.  i rebooted and it came up just fine.  the connection is eth0 too.  i'm enjoying this Asus EEEPC 1005HA, but it sure has its issues to overcome.

---

### Post by shredder12 on 2009-12-30
ifconfig -a shows all the available interfaces, it doesn't restart the connection..
But anyways, i have seen some similar problems.

I think probably reporting a bug on launchpad.net will make sure such problems doesn't occur in later releases.

---

