---
title: "connection not working"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by e4rendil on 2011-06-22
Hello, me too I had this sticky problem with b43 drivers.

Unfortunately, on my Acer Extensa 5620z I'm not even able to connect via ethernet, so I can't download upgrades, driver or whatever.
This was initially with 11.04, so I've decided to get back to 10.04, but the problem persists.

Then, here we go with details:

networking checked - is enabled.
Ip configuration (I've got static local address) - is ok.
Ifconfig - recognizes eth0.
Iwconfig - recognizes wlan0.
Ping - 100% packet loss, always.
dig - goes on timeout.
netstat -an - doesn't show any connection with external address.

What could I do? I'm losing hope :(
Thank you in advance

---

### Post by uRock on 2011-06-22
Can you please post the output of the **lspci** command in a terminal so that we can see exactly what hardware is in use?

Also, have you checked the install disk for quality by booting it, then hitting the spacebar at the first purple screen, then selecting to test the disk?

---

### Post by gordintoronto on 2011-06-22
Are you saying this computer does not have Internet access when you use a wired connection? It should work just fine, any other result is a hardware problem. Maybe a bad Ethernet cable or loose connection.

---

