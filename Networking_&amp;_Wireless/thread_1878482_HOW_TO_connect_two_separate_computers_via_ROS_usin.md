---
title: "HOW TO: connect two separate computers via ROS using bluetooth"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by douglasbrooksjr on 2011-11-09
So, I have been fighting with this for the past 2 days now.  I have two separate computers, each running Ubuntu of course, and each has its own bluetooth dongle (same make and model).  I can get each of the computers to bond to one another, but when I try to telnet via Putty or any other means I get the following error:

> Connection Refused  (#via Putty)

or

> Can't connect RFCOMM socket: Connection refused  (#via rfcomm in the terminal) 

To give you a bit more background, I have also tried to connect each computer using ssh over WLAN.  However, I get the following error:

>  ssh: connect to host HOSTNAME port 22: Connection refused 


It seems like port 22 is blocked somehow, but I have no clue as to how to unblock it.

---

