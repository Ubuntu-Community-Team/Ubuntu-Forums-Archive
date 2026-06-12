---
title: "How to turn off WIFI power management?"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by trherald on 2009-12-21
Hi, and thanks in advance for the help!

I'm trying to figure out how to turn off the WIFI power management (Ubuntu 9.10, eee-PC 1000HE, Atheros 928X).  

I can do it using 'sudo iwconfig wlan0 power off' and it does indeed seem to stabilize the random drops in the wireless network.  

I know I've seen somewhere in this forum which /etc config file to put the change into, but I can't seem to find it now to save my life!

Can somebody please point me in the right direction so that I can turn off power management and have it survive across reboots?

thanks!!!

---

### Post by trherald on 2009-12-21
I think I found a solution (at least it SEEMS to work):

modify /etc/network/interfaces and add:

auto wlan0
iface wlan0 inet dhcp
   wireless-power off

reboot and lo-and-behold iwconfig shows power management off!!

---

### Post by doruktayfun on 2010-03-25
Thanks for posting this :D

---

### Post by Jepeppi on 2011-05-25
I tried what you said in 11.04, and it totally ballsed up my networking. My menu bar looked like it was from an older version, and it wouldn't connect at all (and if i went to iwconfig, it said that my power management was still on). How can I basically do what you want to do, but in 11.04?

---

### Post by Jepeppi on 2011-05-25
I found a solution:

Go to /etc/pm/power.d and create a file called wireless. In it write:

#!/bin/sh
/sbin/iwconfig wlan0 power off
and you should be fine! From what I can work out, this basically overrides ubuntu's default power management regarding wireless. Seems to be working for me on 11.04.

---

### Post by brubbel on 2011-09-26
Adding the "wireless-power off" to /etc/network/interfaces works!

Thanks a lot!

---

