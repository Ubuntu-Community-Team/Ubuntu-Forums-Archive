---
title: "Can`t access local ftp from ubuntu"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by spacedrone808 on 2012-09-09
[LEFT]I have two puters: desktop and laptop. Desk set to Windows 7 with Filezilla ftp server.Ftp is correctly configured. But when i am trying to access it from laptop Ubuntu 12.04  I get the message:** No address associated with hosthame**

All machines get internet from Asus WL500gpv2 router (192.168.1.1). Desktop (192.168.1.2) connected with wire and notebook (192.168.1.3) connected wirelessly.  

Laptop pings desktop machine...Your thoughts about that?
[/LEFT]

---

### Post by JRV on 2012-09-09
Try it from the command line and see what error messages you get.
```

nautilus ftp://Windows_Hostname

```

---

### Post by spacedrone808 on 2012-09-09
> **JRV said:**
> Try it from the command line and see what error messages you get.
```

nautilus ftp://Windows_Hostname

```

[IMG]http://rghost.net/40272951/image.png[/IMG]

---

### Post by spacedrone808 on 2012-09-09
when i try to do nslookup command from ubuntu, here what i`ve got:

> nslookup **spacedrone808pc**
Server:        127.0.0.1
Address:    127.0.0.1#53
** server can't find spacedrone808pc: NXDOMAIN[B]

spacedrone808pc[/B]  is windows host name of 192.168.1.2

here my hosts file [just in case]

> 
127.0.0.1    localhost
127.0.1.1    spacedrone808-z930   --> laptop
192.168.1.2    spacedrone808pc

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

