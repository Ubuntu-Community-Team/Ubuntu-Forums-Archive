---
title: "Firestarter no access to server"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by Constantinff on 2011-12-22
On my server I have installed Firestarter which shares the eth0 connection to a wireless USB stick using some tutorial on the forum. Everything works except that the web server or any other serves running on my server is unaveable to the ones connected with wireless. Probably Firestarter does not allows those connections. How can I check this and how to make available the required serveses for the ones connected throw the wireless?

---

### Post by CharlesA on 2011-12-22
You'd have to allow those services access from wlan0, or whatever your wireless card is named.

It would be a better idea to use straight iptables or something like ufw to manage firewall rules instead of using firestarter, especially if the machine is a server.

---

