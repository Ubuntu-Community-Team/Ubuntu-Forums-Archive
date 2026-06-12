---
title: "Wireless !(not)Working with xubuntu &amp;&amp; bcm43xx"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by penis on 2009-05-26
Hi all, 

I've found really great help on this forum in the past, and searched for my current particular problem.  (I found a couple of great ideas, but I still can't figure my problem out.)  

I have a fresh install of Xubuntu on my old laptop.  Everything works great, except for the wireless.  It says my hardware is "disabled."  I'm dual booting with Windows 7, and I know that the Wireless card has always worked fine.



[IMG]http://i44.tinypic.com/23m0civ.png[/IMG]
(result of 'sudo lshw')

[IMG]http://i44.tinypic.com/vzvt54.png[/IMG]

Thanks in advance for help.

---

### Post by penis on 2009-05-26
So I need to do this?

[http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx](http://linuxwireless.org/en/users/Drivers/b43#fw-bcm43xx)

---

### Post by penis on 2009-05-26
Alright.  I got all of the firmware files from the above link, but I can't add them to my /libs/firmware directory.  It's read only and I don't know how to add them.  Can't seem to log on as "root."  

Ideas?

---

### Post by kerry_s on 2009-05-26
no, no need to manually install, it's in the repo's.
in that terminal:
[B]sudo apt-get update
sudo apt-get install b43-fwcutter[/B]
or
use **synaptic** to install

make sure you have all your repos on.

---

### Post by penis on 2009-05-26
Hrmm.. Got the .fw files in my firmware folder, but the device is still showing disabled, and that the network is down.  Not sure what to do at this point.  ?

[IMG]http://i43.tinypic.com/kdmrfp.png[/IMG]

---

### Post by kerry_s on 2009-05-26
reboot, so it can fully load.

---

### Post by penis on 2009-05-27
Thank you for your continued help.  It's very appreciated.  

I restarted a couple of times before posting that response yesterday.  

I'm somewhat familiar with Linux, but I've never used it as a primary OS; it is very possible that I'm overlooking something, but I feel like this should "just work."  

It [the wireless] always has in the past when I've ran Linux from a jump-drive or cd, ya know?

---

