---
title: "wired connection not working"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by mahendrahpu on 2009-12-30
hello
 
i installed wicd network manager but now it is not started so please tell me how we can change my ip address so we can use wired  internet.
 
Thanks

---

### Post by Project PWNED on 2009-12-30
sudo dhclient eth0

---

### Post by mahendrahpu on 2009-12-30
vaibhav@vaibhav-laptop:~$ sudo dhclient eth0
[sudo] password for vaibhav: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:26:22:9a:3f:50
Sending on LPF/eth0/00:26:22:9a:3f:50
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 
 
 
so............

---

### Post by shredder12 on 2009-12-30
how are you actually trying to connect to internet?

---

### Post by mahendrahpu on 2009-12-30
Actually yesterday night i use internet via wire and fill all the ip . getway, netmask an  wicd network manager all that in my lab.
Now i want to use wire for internet in my room. but wicd network manager is not running so i could not change ip , getway, netmask etc address in wicd network manager resulting it is not working.

so how we overcome from this

---

### Post by shredder12 on 2009-12-30
I have never use wicd but by its not working if you mean that the deamon is stopped then you can make it work by starting wicd service..
```
sudo /etc/init.d/wicd start
```
I am not sure what the service name( i hav used wicd here) is but you can start it in a similar way.

---

### Post by mahendrahpu on 2009-12-30
not working yet....
could you tell me which network manager we can install newin place of wicd

---

### Post by shredder12 on 2009-12-30
have you tried restarting the system..
you may try network-manager.
```
sudo apt-get install network-manager
```

---

### Post by mahendrahpu on 2009-12-30
sudo apt-get install network-manager
failed because of without internet connection

---

### Post by shredder12 on 2009-12-30
well.. it can be easily fixed.. (i hope :) )
are you using static ip or dhcp? 

if its static and your wired interface is eth0 then add this entry in your /etc/network/interfaces file, ofcourse add your own IP info.
```
auto eth0
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.1
```

and if its dhcp use this
```

auto eth0 
iface eth0 inet dhcp
```

---

