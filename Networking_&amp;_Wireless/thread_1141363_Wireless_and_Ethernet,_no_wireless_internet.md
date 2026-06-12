---
title: "Wireless and Ethernet, no wireless internet"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by toreil on 2009-04-28
I have a headless PC running Jaunty which has all my video files stored on it and I connect my laptop to it directly through ethernet (without router or switch) to access all those video's. My problem is that the server is reliant on wlan to get its internet, which is fair enough but whenever the ethernet cable is plugged in to the PC it uses this as my default connection and tries to get its internet through the ethernet which is not possible. I had a similar problem on my MacBook but changed the default connection to being wireless instead of the wired connection which solved it, is there anyway to do this in ubuntu or not?

---

### Post by ktechman on 2009-04-28
I believe you can make a change in network manager to use the wired connection as loopback. Rightclick on the network daemon and edit connections change  the eth0 connection or whatever your wired is using try to not connect automatically or link-local only under the ipv4 settings. 


Regards Ktechman

---

### Post by toreil on 2009-04-28
Thanks for the quick reply although your solution didn't work for me, turns out I had to set the DNS to the same as the wlan connection and the internet just started working. Don't really understand why but if it works it works i guess.

---

### Post by lapi on 2009-04-28
OK, i have one problem about wireless i cant have connection. Today i was downloaded ubuntu 9.04 and when i want to put ip,dns,gateway its not like on 7.10 gutsy gibbon.
In manual i see some  MAC adress:( and i cant put ip,dns,gateway in some fields (missing).
Can anybody tell me step by step what  imust do i am very confused what to type in fields manual for wireless connection?  THANKS:popcorn::P

---

### Post by toreil on 2009-04-28
Sure,

Go to network connections --> IPv4 Settings

In Method go to manual and you should be able to change all the settings there

---

### Post by lapi on 2009-04-28
Ok Toreil bro i will try that solution just tell me one more thing.When i put manual all information then, i must go in terminal and type PPPOECONF like on gutsy gibbon,right?

---

### Post by cooprocks123e on 2009-09-07
thanks, it worked! BTW, you can turn on connect automatically.:biggrin:

---

