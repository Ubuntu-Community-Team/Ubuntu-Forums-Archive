---
title: "Fresh Karmic instal cannot connect to office internet"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by bish84 on 2010-02-04
hi all,
After trialling ubuntu on my home comp, and getting brilliant results, i've now migrated my work computer too. 

Now, i can't connect to the internet or office network. I'm on a small office wired network. When i was on XP all the settings were on 'áutomatic' - didn't need to input an IP, DNS, subnet etc. Now i Can't even ping the router.

I've browsed around various other threads and can't find a working solution. I've tried inputting various settings in ubuntu connection settings, but still cannot get it working. (was hoping it would be automatic, as it was on my home comp).

Any ideas? Advice would be much appreciated - Really don't want to have to go back to XP just because of this!

Ian

---

### Post by Charly85551 on 2010-02-06
Hi bish84,
can you show the results of:
- sudo gedit /etc/network/interfaces

if there is no entry for eth0 try this:
- same start as above and then enter:
- auto eth0
- iface eth0 inet dhcp

after storing the above you need to restart the interface with:
- sudo /etc/init.d/networking restart

The other open question is what are the details of your office network router? You may be able to force your pc into a certain setup if you have details.

cheers

charly85551

---

