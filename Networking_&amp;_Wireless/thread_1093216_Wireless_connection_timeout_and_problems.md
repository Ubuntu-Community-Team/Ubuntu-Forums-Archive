---
title: "Wireless connection timeout and problems"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by joum on 2009-03-11
Hi guys!

I'm having some problems using the wireless network at my college campus. It's the "eduroam" network used in many european colleges.

I CAN actually connect to the wireless network with a simple tutorial from the system administrators and using ubuntu's network manager.

The network is hidden and uses PEAP/MSCHAPv2. Using the wireless connection in Windows XP or Vista has no problem whatsoever, but in ubuntu, the connection "timesout" after 15 minutes or so. 

In Windows what actually happens is that the wireless connection changes its ID from (ie) "eduroam 45" to "eduroam 46", but the connection is maintained seamlessly. 

In ubuntu, I get disconnected after a while and I have to restart the wireless controller, delete the configurations I had made with the network manager and redo the whole process, which is a pain in the a/&#, because it takes about 5 minutes every 15, and makes working under ubuntu very hard.:(

I can post more system info here if someones tells me how. Any ideas will be very, very welcome.

Thanks in advance!

---

### Post by joum on 2009-03-12
bump...

---

### Post by joum on 2009-04-01
bump

---

### Post by joum on 2009-04-25
Well, after some research **I finally solved this problem**.

The wireless network I was trying to connect to was hidden and the LDAP authentication server here at campus has a "feisty" temper (as in, stupid thing won't work properly).

I solved the problem described above by using **Wicd** instead of ubuntu's native **Network Manager**. Not sure why one works fine and the other doesn't, but hey!... :confused:

Since the network is hidden, I still have to configure some stuff to make it auto connectable when in network reach, but at least it doesn't timeout and force me to redo the whole process.

So by now, I can finally say I have successfully migrated to Ubuntu for the first time! Whooraay! :)

---

