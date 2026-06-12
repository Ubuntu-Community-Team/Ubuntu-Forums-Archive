---
title: "Ubuntu Server causes modem to crash (&quot;No internet access&quot;)"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Eraknelo on 2010-07-28
Hello,

I have just (finally) finished installing Ubuntu Server on my older stationary PC. After loads of trouble with installing using a USB thumb drive, I have switched over to doing it with a DVD-R. First attempt was using "Universal USB Installer v1.7.4", no luck, it tried to copy the files from a CD-ROM, but obviously I was using a thumb drive.
Then I tried "UNetbootin", this is where I first got the problem. It was stuck at "Retrieving apt...". I went to my laptop, and tried to go on the internet. It said "No internet access.". Turned out, all other computers on the network had it as well. Rebooted router, nothing happened. I had to reboot the modem in order for everything to work again.
So, next up, I tried the DVD installation. This time, it got a lot further. However, all computers started showing "No internet access" again, I waited a while, and the setup finished anyways. Reset modem, reset router, the server booted, everything was fine. Until I tried the command "sudo apt-get update", the same problem occurred! Got about 33%, then it failed because of no internet access.
I have found another post of someone with the same problem: [http://ubuntuforums.org/showthread.php?t=1214565](http://ubuntuforums.org/showthread.php?t=1214565)

I have no idea how to fix this! Found nothing on  the internet.

Please help me!
 
-René

EDIT: I have found the (as far as known) one and only solution: [http://ubuntuforums.org/showpost.php?p=9665985&postcount=6](http://ubuntuforums.org/showpost.php?p=9665985&postcount=6)

---

### Post by iponeverything on 2010-07-28
try dropping the MTU to 1492.

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

---

### Post by Eraknelo on 2010-07-28
> **iponeverything said:**
> try dropping the MTU to 1492.

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

Thank you for the quick reply! I will try it in a few hours, when nobody else is using the internet. If I do it now, you might not see me post on this forum ever again :P

---

### Post by Eraknelo on 2010-07-28
> **iponeverything said:**
> try dropping the MTU to 1492.

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

It didn't work. Same problem occurs. I'm stepping over to normal Ubuntu, the desktop edition. Thank your for your helpful suggestion anyways :)
I would still like to continue this thread, in order to get an answer, or maybe come to the conclusion that it is a bug. If the error gets fixed, I'd still love to re-install Ubuntu Server.

-René

---

### Post by Eraknelo on 2010-07-28
I have just found out that the Ubuntu desktop installation has the same problem!

P.S. The actual modem completely crashes, so, even the phone doesn't work anymore. It's not just the router. And I found out that I don't have to reset the router, only the modem. I'm really desperate to find a solution to this, I cannot get another modem.

---

### Post by Eraknelo on 2010-08-01
Ok, I fount the problem! It's rather unfortunate, but the router was causing the problem. I have an Linksys WRT160Nv2 router, with a FON router plugged in to it. I now switched them, so that the FON router is the main one, and connected the Ethernet cable of the computer directly into the FON router. I have not found another way. 32-bit, 64-bit, desktop, server, all of these versions had the problem on the Linksys router.

Summary: Get an other router!

---

