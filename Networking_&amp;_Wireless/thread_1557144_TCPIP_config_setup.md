---
title: "TCP/IP config setup"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by NigelRen on 2010-08-20
I've recently bought a server and want to be able to set up networking to allow various things, but not sure where to start.
The server is running Ubuntu 10.04 and dual nic ( eth0, eth1 ), atm I've only connected one cable to an old wireless router I had ( I just want to use it as a hub rather than a router - unless using it as a router would help ). Then a cable goes from the router to my laptop eth0 connection ( the laptop is currently running 9.10 ).  The internet is connected via a USB dialup ( connected as ppp0 ).

I've tried setting the server eth0 on the server and eth0 on the laptop as static IP and the machines can connect OK.  But on the laptop when I connect to the internet, I can't connect to the server.  It could be trying to route the traffic over the ppp0 connection, I would change routing to 192.168 to use eth0 - but again not sure how.
I would like to be able share my internet connection, but when I go to network connections to change the IPv4 settings to shared, the only options I get are Automatic (PPP) and Automatic (PPP) addresses only.

Any help would be great - even if it is 'RTFM' - as long as it points me to a web page with some useful instructions on.
Thanks

---

### Post by Iowan on 2010-08-20
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is an ICS help page.
What are the results of **route -n**?

---

### Post by sikander3786 on 2010-08-20
For easy ICS there is [Firestarter]("https://help.ubuntu.com/community/Firestarter"). A nice gui tool that will configure almost everything with a few clicks, even the firewall.

Regards.

---

### Post by NigelRen on 2010-08-20
> **sikander3786 said:**
> For easy ICS there is [Firestarter]("https://help.ubuntu.com/community/Firestarter"). A nice gui tool that will configure almost everything with a few clicks, even the firewall.

Regards.
I used Firestarter and managed to get it working with a few tweeks on the client machine.:D

Not sure about the routing bit - I did turn off a lot of the functionality of the router just in case it was doing anything.  Checked it with internet connecting from server and RDP'ing to the server.

Thanks for the help!

---

