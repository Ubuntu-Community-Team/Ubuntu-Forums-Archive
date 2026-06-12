---
title: "tricky network setup"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by scales on 2009-05-31
Hi all.  I am running a router/computer which i got setup by following:
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

Ideally i would like to share a printer and the cdrom of my router/computer, here is a rough idea of the connections

internet--eth0-->ubuntu_router--wlan0-->computers 1 & 2

if i bridge the wlan0 to eth0, i am just re-directing traffic, i dont actually get to talk to the ubuntu-router right? is there anyway i could both bridge the connection and use say openssh or share a printer from ubuntu-router with connecting computers?

---

### Post by superprash2003 on 2009-05-31
internet connection sharing will do the trick...all machines will be able to access each other.. [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html)

---

### Post by scales on 2009-05-31
ya know i thought it would be that simple! darn i spent so much time hunting for drivers and stuff.  doesnt require "master" mode? and i would be able to connect multiple machines to the single broadcasting wlan0?

EDIT:  no i still need the wireless adapter to operate in master mode.  still could work...?

---

### Post by scales on 2009-05-31
on another note, could i share a printer from the host/server too?

---

### Post by dmizer on 2009-05-31
You can do all of that, but I wouldn't personally advise it. The more services you have running on your gateway, the more likely you are to get compromised unless you're really careful with your configureation. And even then, if there's a security hole in one of your services it won't matter how carefully you've configured things.

If you really NEED both a computer gateway and a local server on the same machine, then I suggest running a dedicated gateway independently in a virtual machine. Otherwise, I suggest you use a wireless router and use your server to share whatever file/printing/networking services you need.

---

### Post by superprash2003 on 2009-06-01
you could always try flushing your iptables . It could be that firestarter or ufw is overwriting it..

---

