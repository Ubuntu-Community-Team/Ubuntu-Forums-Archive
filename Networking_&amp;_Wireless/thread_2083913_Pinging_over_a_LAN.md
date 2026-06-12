---
title: "Pinging over a LAN"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by PalapaGuy on 2012-11-14
I am able to ping one computer from another  within my office over the router.  But is there a way to make the  receiving computer report locally that it has been pinged? 
 
Both computers are running Ubuntu 12.04.

---

### Post by gerowen on 2012-11-14
You want the computer receiving the ping to report to a user that it has been pinged, or do you want the report to come back to the computer that sent the ping?

The easiest method without creating custom scripts and whatnot would be to install Firestarter.  It's a free firewall application that has a very simple GUI, and a log tab that will display every incoming connection attempt that you don't have a rule set for, including pings.  If you minimize it to the system tray and something happens, its icon will turn into a red lightning bolt to catch your attention and let you know something else is going on.

You could get all fancy with some scripts calling zenity to display a dialog, but I think Firestarter would be faster.

---

### Post by raja.genupula on 2012-11-14
ok i got something for you 

[http://serverfault.com/questions/448541/how-to-know-who-ping-my-computer](http://serverfault.com/questions/448541/how-to-know-who-ping-my-computer)

---

