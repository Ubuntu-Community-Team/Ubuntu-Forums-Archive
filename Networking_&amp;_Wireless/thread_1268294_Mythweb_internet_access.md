---
title: "Mythweb internet access"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by johnvan on 2009-09-16
I've got mythtv working perfectly I can access mythweb on my local network but can't get things set up externally. I used the mythbuntu control center to set up the password.
I changed the port on mythweb to 5631 and I know this worked because I need to enter :5631 after my ip address to get mythweb on my home network.
I am 99% sure my router isn't blocking the port because if I open transmission bittorrent and select port 5631 it shows it as open. 
Online port scanners show all of my ports as stealth. (unless I'm running transmission bittorrent and test on that port)
I believe the problem might be with permissions somewhere, it seems like mythweb (apache2 ?) is either rejecting all requests or is not listening to ports externally.
My knowledge level is pretty low on this so any pointers would be great.

---

### Post by johnvan on 2009-09-16
One more piece of info, I tried setting up remote desktop.  Locally it works. Port 5900 is showing open but I cannot access it with the external ip address. (connection closed)

---

