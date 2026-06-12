---
title: "Network connection activation"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by SupremeSpike on 2006-06-08
I go into networking under adminstration, and my wireless connection shows up as eth1. I activate it and setup all my network options such as SSID and WEP keyIt is a broadcom wireless chip I recieved with my laptop zx5000. After I click activate it activates, the only problem is I am not conntected to the wireless. I exit the networking screen, and reopen it and it says my network connection is not active. I'm confused.

---

### Post by ComplexNumber on 2006-06-08
add 'modprobe ndiswrapper' statement to /etc/rc.d/something.local file. i can't remember the name of the 'something', but there is only 1 file there with *.local. 

btw why don't you think that you're connected? add the notification applet to your panel. that should give you some clues.

---

### Post by SupremeSpike on 2006-06-08
I looked in etc there is no folder named rc.d, there is rc0.d rc1.d and etc.  In each of those there is no file with the ext *.local.  Thank you for trying!  Also when I try to set up the notification panel it doesn't show up a small dotted line displays instead.  I know I am not connected because the internet doesn't work after I enable the card. When I go back to the network settings after hitting ok, the connection is not activated anymore.

---

