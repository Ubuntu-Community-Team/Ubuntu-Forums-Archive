---
title: "Dhcp3"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by john2010 on 2010-07-19
having a problem getting this to run here's my config
i'm able to use samba between the ubuntu box and windows box
but the dhcp3 server will not start

ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

# Local Network
subnet 192.168.0.0 netmask 255.255.255.0 {
    option netbios-name-servers 192.168.0.52;
    option domain-name "johnubuntu.local";
    option domain-name-servers 192.168.0.250 , 192.168.0.251;
    option broadcast-address 192.168.0.255;
    option subnet-mask 255.255.255.0;
    option routers 192.168.0.1;
    range 192.168.0.50 192.168.0.55;
    }
[U]
[[IMG]http://img835.imageshack.us/img835/1100/ifconfig.png[/IMG]]("http://img835.imageshack.us/i/ifconfig.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

[]("http://imageshack.us")[[IMG]http://img833.imageshack.us/img833/8638/routes.png[/IMG]](http://img833.imageshack.us/i/routes.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
[/U]

---

### Post by Iowan on 2010-07-19
Having both NIC's in the same subnet usually causes problems. If the DHCP server will share it's Internet connection, [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page might be useful.

---

### Post by john2010 on 2010-07-19
> **Iowan said:**
> Having both NIC's in the same subnet usually causes problems. If the DHCP server will share it's Internet connection, [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page might be useful.

not sure i understand but i tried to give one to eth0 192.168.1.x but then it got no internet connection.
it would only connect to internet with 192.168.0.x

---

### Post by Iowan on 2010-07-19
If your router is at 192.168.0.1,eth0 will need to be in that subnet, and you may need to change the subnet (and DHCP range) for eth1. Otherwise, you could change the router address and eth0.
Gets a li'l involved, either way...

By the way... what's at 192.168.0.254?

---

### Post by john2010 on 2010-07-20
> **Iowan said:**
> If your router is at 192.168.0.1,eth0 will need to be in that subnet, and you may need to change the subnet (and DHCP range) for eth1. Otherwise, you could change the router address and eth0.
Gets a li'l involved, either way...

By the way... what's at 192.168.0.254?

my router for the main incomming basically the gateway.
could u explain in detail what i should change would help a lot .
i tried to setup eth1 on a 192.168.1.x and changed the dhcp subnet to 192.168.1.1 and range of 192.168.1..50 192.168.1.55 and no go.

---

### Post by Iowan on 2010-07-20
What address did you give eth1? It will need to be outside the DHCP range - but still inside the subnet.
"No go" means the DHCP server still won't start?

---

### Post by john2010 on 2010-07-21
> **Iowan said:**
> What address did you give eth1? It will need to be outside the DHCP range - but still inside the subnet.
"No go" means the DHCP server still won't start?

i gave eth1 192.168.1..1, 255.255.255.0 

i'm able to ping it from the windows box and the linux box

the server wouldn't start after changes i made.

eth0 is my internet source 192.168.0.50, 255.255.255.0, 192.168.0.254
i want the DHCP server to issue leases on eth1 to my windows box for internet sharing.

192.168.0.254 is my gateway "router"

---

### Post by Iowan on 2010-07-21
Post the DHCP config file.
 What sort of error message is generated?

---

### Post by john2010 on 2010-07-21
> **Iowan said:**
> Post the DHCP config file.
 What sort of error message is generated?


ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

# Local Network
subnet 192.168.0.0 netmask 255.255.255.0 {
    option netbios-name-servers 192.168.0.52;
    option domain-name "johnubuntu.local";
    option domain-name-servers 192.168.0.250 , 192.168.0.251;
    option broadcast-address 192.168.0.255;
    option subnet-mask 255.255.255.0;
    option routers 192.168.0.1;
    range 192.168.0.50 192.168.0.55;
    }
it doesn't give any in terminal but in webmin it doesn't appear to be running.

---

### Post by Iowan on 2010-07-21
> **john2010 said:**
> ...i tried to setup eth1 on a 192.168.1.x and changed the dhcp subnet to 192.168.1.1 and range of 192.168.1..50 192.168.1.55 and no go.:confused:  I thought DHCP and eth1 got moved to 192.168.1.X...

---

### Post by john2010 on 2010-07-23
> **Iowan said:**
> :confused:  I thought DHCP and eth1 got moved to 192.168.1.X...

yeah it did eth1 is 192.168.1.10 and i changed up my conf file to relate to that but still not working.

---

### Post by BarryDocks on 2010-07-23
John

I assume this machine is acting as an internet gateway for machines on your internal LAN?  It is very confusing having the internal IP address pool the same as the one from your router which I assume the other NIC is connected to?

First, I would suggest using a completely different IP range for your lan, something like 10.10.10.x  that way things are more straight forward to sort out (this may cause problems if you have already set up services like DNS and samba but it's not too hard to change)

incidentally what version of ubuntu are you running, I not that webmin is not fully working with 10.04 yet, so you might find the DHCP server is actually running, try:
```
ps -e | grep dhcpd
``` 

Also ensure /etc/default/dhcp3-server has the correct nic card listed (ie the one being used by the internal lan)

Please post any messages in the syslog after starting dhcpd

---

### Post by john2010 on 2010-07-23
> **BarryDocks said:**
> John

I assume this machine is acting as an internet gateway for machines on your internal LAN?  It is very confusing having the internal IP address pool the same as the one from your router which I assume the other NIC is connected to?

First, I would suggest using a completely different IP range for your lan, something like 10.10.10.x  that way things are more straight forward to sort out (this may cause problems if you have already set up services like DNS and samba but it's not too hard to change)

incidentally what version of ubuntu are you running, I not that webmin is not fully working with 10.04 yet, so you might find the DHCP server is actually running, try:
```
ps -e | grep dhcpd
```Also ensure /etc/default/dhcp3-server has the correct nic card listed (ie the one being used by the internal lan)

Please post any messages in the syslog after starting dhcpd

yeah i want to use it as a gate way for my windows box and yeah eth0 is the internet source. 
i want to use eth1 to lease ip for my windows box or my lan for internet sharing.

---

### Post by BarryDocks on 2010-07-24
If you want a simple method for internet connection sharing and a good fire wall, try shorewall - there is also a good webmin module that makes administration easy.  I suspect this will be what you are looking for:
[http://www.shorewall.net/two-interface.htm]("http://www.shorewall.net/two-interface.htm")

or if you have a GUI try firestarter:
[http://www.fs-security.com/]("http://www.fs-security.com/")

---

### Post by john2010 on 2010-07-26
> **BarryDocks said:**
> If you want a simple method for internet connection sharing and a good fire wall, try shorewall - there is also a good webmin module that makes administration easy.  I suspect this will be what you are looking for:
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

or if you have a GUI try firestarter:
[http://www.fs-security.com/](http://www.fs-security.com/)

thanks to **BarryDocks** i managed to get this working finally i upgraded to the latest ubuntu 10.04
re-installed DHCP3

---

