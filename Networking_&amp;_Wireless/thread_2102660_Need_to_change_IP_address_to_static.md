---
title: "Need to change IP address to static"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by sagitta007 on 2013-01-07
Read a few articles off the Internet on this, but all seem to say you need to see eth0 in interfaces buuut this is what I see....
auto lo
iface lo inet loopback

~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/network/interfaces" 3 lines, 32 characters

Help me out?

---

### Post by Bucky Ball on 2013-01-07
Welcome to the forums. You want to change from dhcp to static? Please give more info, for instance what release and flavour you are using.

You can do it easily in Network Manager and don't need to touch the interfaces file. IPv4 Settings>Method>Manual. Make the changes. You will obviously need some info like the address of you gateway and DNS details.

---

### Post by ahallubuntu on 2013-01-07
Try this:

[http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/](http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/)

---

### Post by efflandt on 2013-01-08
The reason /etc/network/interfaces is mostly empty is because NetworkManager is the usual Ubuntu network configuration tool and it cannot manage or control anything in the interfaces file.  The interfaces file is typically used if you do NOT have NetworkManager.

The icon for configuring networking is typically on the right side of the upper bar in X.

---

### Post by Bucky Ball on 2013-01-08
Just right click the network icon and Edit Connections ...

---

