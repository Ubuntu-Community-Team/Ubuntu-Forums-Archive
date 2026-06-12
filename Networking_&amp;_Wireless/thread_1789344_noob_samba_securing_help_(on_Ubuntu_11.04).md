---
title: "noob samba securing help (on Ubuntu 11.04)"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by banff2010 on 2011-06-23
Could someone explain the following commands to me please?
 
```
*hosts allow = 127.0.0.1 192.168.2.0/24 192.168.3.0/24*
*hosts deny = 0.0.0.0/0*
```What does /24 mean? 
How do I find equivalent numbers for 192.168.2.0 in ubuntu 11.04?

```
interfaces = eth* lo bind
interfaces only = yes
```How do I find "eth" for my network.
Thanks a lot.

I got these commands from the manual.

---

### Post by josephmills on 2011-06-23
> **banff2010 said:**
> Could someone explain the following commands to me please?
 
```
*hosts allow = 127.0.0.1 192.168.2.0/24 192.168.3.0/24*
*hosts deny = 0.0.0.0/0*
```What does /24 mean? 
How do I find equivalent numbers for 192.168.2.0 in ubuntu 11.04?

```
interfaces = eth* lo bind
interfaces only = yes
```How do I find "eth" for my network.
Thanks a lot.

I got these commands from the manual.
 to find your eth ip and mac just do a ```
ifconfig
``` or click on the network managers icon and select connection info and that will tell you all that. so it is saying allow host 127,0.0.1 and 192.168.2.0 though 24 hope that this helps

---

### Post by Dangertux on 2011-06-23
192.168.0.0/24 refers to the CIDR (classless interdomain routing protocol) for a class c network

So saying 192.168.0.0/24 would be the same as saying 192.168.0.0 with a subnet mask of 255.255.255.0

/24 = class C
/16  = class B
/8 = class A

CIDR can be used to represent more specifically than a conventional subnet for instance 192.168.0.0/22 represents the next 1024 addresses. 

So a direct answer to your question 192.168.2.0/24 =192.168.2.0-192.168.2.255

Hopefully that helps clarify.

---

### Post by banff2010 on 2011-06-24
Thank you to both of you. I still have to do more reading. In the meantime I decided to turn off my computer with samba server when I don't use it as a precaution. I have disabled guest login, but ..

Thanks again for reading and clarifying.

---

