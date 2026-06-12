---
title: "Networking problem ... again ..."
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Luk8 on 2006-06-06
I just intalled Dapper and the problem that I had with the network connection in breezy is back. 

I have a Realtek card , for which the OS loads 2 drivers : 8139cp and 8139too . After rmmod / modprobe each I found that only 8139too work , and makes my ethernet interface to be recognized . 

I normaly have to get a dynamic IP based on my network card's MAC ( hw adress ) , but I couldn't succed in making ubuntu get that along with other data automaticly , and I did the same thing I did in breezy: edit /etc/network/interfaces and the eth0 part looks like this:
```

auto eth0
iface eth0 inet static
        address 86.124.XXX.XXX
        netmask 255.255.252.0
        gateway 192.168.2.1

```

I have the following data:
IP:  86.124.105.XXX
subnetmask: 255.255.252.0
gateway 86.124.XXX.XXX
DHCP server: 213.157.176.6
DNS1: 213.157.XXX.XXX
DNS1: 213.157.XXX.XXX
and my network card's mac is: 4C-00-10-3A-91-DF .

How should my interfaces file look like considering the above ( and not using DHCP ).

Also updtated rezolv.conf to math my DNS servers that my ISP provide me with .
I tried disabling IPv6 ( edited /etc/modprobe.d/aliases ) but I have no ideea if  I succeded that because when I **ifconfig eth0**
an IPv6 adress still apears.

when I run ifconfig eth0 some of my data appear correct ( IP , netmask .. ) but no HW address appears ( HWaddr:00-00-00-00-00 ) , so I assume that actually the system can't find my network card .

Ofcourse , pinging the gateway brought no response back.

What can I do to fix that ? 

And also , what other info should I provide ? ( considering that I can't copy/paste or save data on anything - floppy unit doesn't work in dapper so far ).

PS: thank you and sorry for my poor english .

---

