---
title: "Static Internet Protocol"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by Colo2 on 2009-05-02
Hey guys, I need a static network IP. I have ports forwarded for 192.168.1.101 and I need my server PC (ubuntu) to have that IP. Trouble is ive only ever done this on windows before. can someone help? 

Thanks :)

Ubuntu 8.10 
Ethernet connection


thanks ;)

---

### Post by chili555 on 2009-05-02
Remove, if it's still there, Network Manager.```
sudo gedit /etc/network/interfaces
```Make it read like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

```Substitute your gateway, if it's not 192.168.1.1. Proofread, save and close *gedit*. Then do:```
sudo /etc/init.d/networking restart
```You should be all set!

---

### Post by Colo2 on 2009-05-02
```
sudo /etc/init.d/networking restart
```

when I did that, I got a jolly old message:

* Reconfiguring network interfaces...
/etc/network/interfaces:5: duplicate interface
ifdown: couldn't read interfaces file "etc/network/interfaces"
/etc/network/interfaces:5: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"         
                                                                                        [Fail]

:( /trouble!

---

### Post by Colo2 on 2009-05-02
No one any ideas? :(

By removing the line in bold:

> auto lo
**iface lo inet loopback**

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

I managed to get rid of the error, but when I rebooted and did ifconfig, I found out that its still given me a random IP.

---

### Post by chili555 on 2009-05-02
Please do:```
cat /etc/network/interfaces > interfaces.txt
```A text file will be created called *interfaces.txt*. Please post it here.

---

### Post by Colo2 on 2009-05-03
auto lo

auto eth0
iface lo inet loopback
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1


that right?

---

### Post by chili555 on 2009-05-03
No, sir. It should be:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
```Then please do:```
sudo /etc/init.d/networking restart
```Let us know about any errors.

---

### Post by Colo2 on 2009-05-03
Perfection, thank you so much for the help man!!!

---

