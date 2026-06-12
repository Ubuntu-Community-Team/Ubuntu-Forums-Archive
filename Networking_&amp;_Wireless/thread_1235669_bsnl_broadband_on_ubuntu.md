---
title: "bsnl broadband on ubuntu"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by newbietolinux on 2009-08-09
I have a bsnl broadband connection and the modem is plugged to ethernet port. at first it was configured to connect to the internet as soon as i plugged the modem to the power. but now i have to manually dial the connection with my username and password. 

when it was automatically connecting, i could access internet form linux. but after having to manually enter the username and password to connect, i am not able to connect to the internet from linux. i tried this solution posted in this forum. but it is not working for me..

> you can use
sudo pppoeconf
command in the terminal.It ask you a series of yes or no questions and your username and password.
Once you are done with it you can use the command
pon dsl-provider
to start your connection and
poff dsl-provider
to end your connection.

please help me....

---

### Post by zkriesse on 2009-08-09
Do you have a regular DSL/Cable or something else that you can use?

---

### Post by newbietolinux on 2009-08-09
its a regular fixed cable dsl modem...

i got this from plog command in terminal...

Aug 25 16:31:46 ubuntu pppd[9301]: pppd 2.4.4 started by root, uid 0
Aug 25 16:31:51 ubuntu pppd[9301]: PPP session is 10908
Aug 25 16:31:51 ubuntu pppd[9301]: Using interface ppp0
Aug 25 16:31:51 ubuntu pppd[9301]: Connect: ppp0 <--> eth0
Aug 25 16:31:51 ubuntu pppd[9301]: CHAP authentication failed: User not found
Aug 25 16:31:51 ubuntu pppd[9301]: CHAP authentication failed
Aug 25 16:31:57 ubuntu pppd[9301]: Connection terminated.
Aug 25 16:31:57 ubuntu pppd[9301]: Modem hangup

please help me.....

---

### Post by newbietolinux on 2009-08-25
i tried to access my modem through 192.168.1.1 but couldn't access it...

---

