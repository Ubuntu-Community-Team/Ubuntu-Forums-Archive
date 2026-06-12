---
title: "Cant get a IP address"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by ali_williams on 2009-08-05
Ok I have had something weird happen to my ubuntu 8.10 box. After a bad storm I found my cable modem was dead. I replaced it only to find my ubuntu box can not get on the internet so i did
>ifconfig

I can not get a ip address so i did
>sudo ifconfig eth0 down
>sudo ifconfig eth0 up

still no ip address so i think it is a bad onboard nic. i buy a new nic. put it in the box. it boots up with no ip address so i did
>sudo ifconfig eth1 down
>sudo ifconfig eth1 up

still no ip address what am i doing wrong this normally fixes the issue.

i also tried 
>sudo /etc/init.d/networking restart
and nada

---

### Post by superprash2003 on 2009-08-05
post output of 
1)ifconfig
2)sudo dhclient eth1

---

### Post by Iowan on 2009-08-05
Have you tried a different cable... just to cover all bases?

---

### Post by ali_williams on 2009-08-06
> **superprash2003 said:**
> post output of 
1)ifconfig
2)sudo dhclient eth1

I dont know how to explain it but it works now i turned it off then when i woke up today its up...

---

### Post by MaindotC on 2009-08-06
In the future, to get an IP address from a DHCP server (which could be your access point if you have one, or the ISP's dhcp server) the command is:
```

sudo dhclient <interface_name>

```

---

