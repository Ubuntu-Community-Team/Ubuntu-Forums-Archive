---
title: "Trouble with maverick wireless RT2800PCI"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by sentryab on 2010-11-04
Hi so I just installed 10.10 for netbooks, and apparently it's using the RT2800PCI driver for my wireless NIC in my EeePC 901. That driver is causing havoc with my school network, I keep getting disconnected, and loading websites is really slow.

Now I know that 10.04 uses a different driver RT2860 which seems to work far better on this network.

Any idea on how to change to the driver from lucid. Or does anyone know of an even better solution? I've heard rumors about something called ndiswrapper...

---

### Post by Peter09 on 2010-11-04
Here is a thread which appears to show some solutions.
 
[http://ubuntuforums.org/showthread.php?t=1592731](http://ubuntuforums.org/showthread.php?t=1592731)

---

### Post by not_a_phd on 2010-11-04
What I have found is that there is a solution for you if you only have to deal with one kind of network. I have the exact same configuration as you. By default the system will want to start up with the 2800/2x00 generic drivers. If you do an **lsmod**, you will find that the rt2800, rt2x00, and rt2860sta drivers will all be loaded. You can make your system work as follows:

When logging into a WPA network, you must blacklist the rt2800pci and rt2x00pci drivers. I have found that this works for me at my work network. This allows the rt2860sta driver to load and operate without interference from the generic modules. (The referenced link in Peter09's reply shows how to blacklist these drivers.)

When logging into a WEP network with a shared key, you must blacklist the rt2860sta driver, and allow the rt2800pci and rt2x00pci drivers to do their thing. I have found on my home network, that this works fine on the eeePC901 running 10.10. But, the rt2860sta driver, which works great at work on the open WPA network will not allow me to connect to my WEP network at all. Looking at the syslog, it fails to associate with the network.

For me, this workaround is a pain in the neck and wholly unsatisfactory. In my own (3-weeks and counting) quest to remedy the situation, I have attempted to make the vendor drivers from the RaLink website work for me. I have compiled and installed them in accordance to the instructions found on this forum, and have had partial success. I can connect to both networks now with one driver set. However, I suffer periodic disconnections (every 5-seconds on the WEP, about every 2-5-minutes on the WPA) from the network. I have been attempting to figure out why this is happening, but have had very little help from this forum.

Good luck to you. I recommend you verify what I have said by blacklisting the appropriate drivers in the different environments. Right now, I would say that wireless is irreparably broken on the eeePC901 with Ubuntu, which is a crying shame given that this is a staple showcase platform for the O/S. :mad:

---

### Post by elhrac on 2011-01-22
Any new information on this?

---

### Post by Basickarma on 2011-10-04
I have had this exact problem. I have a sony viao and sometimes it doesn't disconnect for a few minutes after which it can't reconnect. It's very annoying I have all the drivers mentioned above and wish to solve it! :(

---

