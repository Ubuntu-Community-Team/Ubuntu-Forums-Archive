---
title: "Two networks at the same time"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by eloydark on 2009-03-26
Hello ubuntuers,
On my laptop I have Ubuntu 8.10 with a wired and a wireless network card. At work I want to connect to my wired network with static IP with DNS settings etc etc and at home with wireless with DHCP or with static (I don't care which, it's the same to me!) but without ruining my DNS settings for my work. I don't use Network Manager since its' bugs cannot get the wired connection to work so I have my /etc/network/interfaces like that:
 ```
auto eth0
iface eth0 inet static
address XXX.XXX.XXX.XXX
netmask 255.255.255.192
gateway XXX.XXX.XXX.XXX
```
for the work configs and my resolv.conf
```
nameserver XXX.XXX.XXX.XXX
nameserver XXX.XXX.XXX.XXX
```
but since I do not know yet how to configure the wlan I am using the Manager to do so and it erases the resolv.conf every time...
Is there a way to have both settings working? I am using WPA-PSK encryption on my WLAN.
Thx in advance

---

### Post by superprash2003 on 2009-03-27
here try this tutorial.. opendns servers are used here , you can change them accordingly [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by eloydark on 2009-03-27
Maybe I have not expressed myself clearly enough, my problem is not with my nameserver, my problem is that my resolv.conf file is being deleted every time I use Network Manager so I want either the manager to stop messing with the file or me to stop messing with the manager (settings for /etc/network/interfaces for wlan are more than welcome for WPA encryption :lolflag:)

---

### Post by GeeZor on 2009-03-27
Try setting to read only.. that might help..
(r--r--r--)

---

### Post by kinggo on 2009-03-27
try with wicd manger instead of default network manager. I'm using it with setup for 2 different wireless networks and one wired and all works fine after initial setup.

---

### Post by eloydark on 2009-03-28
> **kinggo said:**
> try with wicd manger instead of default network manager. I'm using it with setup for 2 different wireless networks and one wired and all works fine after initial setup.

I can't find any app named like this in the repos :-S

---

