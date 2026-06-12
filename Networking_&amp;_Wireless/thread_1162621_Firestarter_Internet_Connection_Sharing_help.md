---
title: "Firestarter Internet Connection Sharing help"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by Stuart1745 on 2009-05-17
I recently up grade a fedora  server to ubuntu 8.04 server. I loaded gnome on the server and am trying to get firestarter to work to share the Internet to the computers behind it. I had previously used firestarter on the fedora server to do this but ubuntu seams to be giving me some troubles.

what I want is this

eth0 connection to the Internet via dhcp. 10.0.##.## number
eth1 connects to the local network. it needs to have a dhcp server on it and its ip address will be 192.168.0.1

I removed the network manager ( because Im hearing that it only allows 1 Internet connection)

firestarter though is still giving me an unknown error when I try and start the firewall. any help or guidance would be great

---

### Post by superprash2003 on 2009-05-18
could you specify the error?? is it " eth0 is not ready" ??

---

### Post by Stuart1745 on 2009-05-18
ok so here is the error. 

Faild to start the Firewall

an unknown error occurred.

Please check your network device settings and make sre your internet connection is active.


I checked my network settings with system ->administration-> network and both devices look to be configured correctly.

I went to upgrade the server to 8.10 thinking that when an upgrade cleans out config files hat might fix it, it did not( same error). how ever this time when the network manager was reinstalled it shows my 2 NICs and shows that they are not being managed.

---

### Post by Stuart1745 on 2009-05-18
also eth0 does work it gets a dhcp address, and it is able to get on line. 

also this error only popsup when I check the Share Connection check mark in the firestarter gui. (thats also kinda what im trying to do so I cant just leave it unchecked)

---

### Post by superprash2003 on 2009-05-18
you could share you internet connection this way [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html)

---

### Post by ssam on 2009-05-18
have you tried just connecting to both networks with network manager. this definitely works for sharing a ethernet network over adhoc wireless.

---

### Post by Stuart1745 on 2009-05-19
Ok so network manager did not do it how ever. I went through those tutorials and found that it was the DHCP server. I needed to turn it on for firestarter to work.

---

