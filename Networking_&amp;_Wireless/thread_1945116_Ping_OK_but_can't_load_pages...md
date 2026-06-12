---
title: "Ping OK but can't load pages.."
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by eco89 on 2012-03-22
Hi!
I'm using Ubuntu 11.10.
In this days i've installed many programs like Samba, and other app...
Now i've a problem... i can't load web pages with any browser (Chrome or Firefox) but if i use ping command in the terminal it's OK (ex ping 151.50.5.2 or ping google.it), and is ok aMsn too..
but chrome and other browser are off..
i have delete samba now but the situation not change..
i have try to modify the file etc/network/interfaces ..
what i can do??
PS sorry 4 my bad english!:D

---

### Post by jonobr on 2012-03-22
can you ping by name eg google.com
when you get a response, can yuou put the ip address into a browser and see if you can get to the site via IP?

---

### Post by CharlesA on 2012-03-22
If you can ping the hostname, then DNS is working fine.

---

### Post by jonobr on 2012-03-22
fair point CharlesA

My mistake here, OP already mentions ping to name working.

Would recommend posting 
/etc/network/interface
/etc/resolv.conf
/etc/nsswitch.conf

and result of ifconfig to see if there is anything funky going on

---

