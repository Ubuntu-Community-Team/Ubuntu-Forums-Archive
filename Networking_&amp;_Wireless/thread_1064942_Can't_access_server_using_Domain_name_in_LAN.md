---
title: "Can't access server using Domain name in LAN"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by Dex24 on 2009-02-09
Hello I'm fairly new to Ubuntu.  I set up my own webserver and I am unable to reach my server using the domain name inside my local area network.  Outside my network works just fine.  The only way I can access my server inside my LAN is by typing in it's local IP address 192.168.1.100.  I edited my /etc/hosts file using the local IP address with the domain name but still no results. Please help.

---

### Post by rickyjones on 2009-02-09
> **Dex24 said:**
> Hello I'm fairly new to Ubuntu.  I set up my own webserver and I am unable to reach my server using the domain name inside my local area network.  Outside my network works just fine.  The only way I can access my server inside my LAN is by typing in it's local IP address 192.168.1.100.  I edited my /etc/hosts file using the local IP address with the domain name but still no results. Please help.

In the hosts file did you just do "example.org xxx.xxx.xxx.xxx" or did you do "www.example.org xxx.xxx.xxx.xxx"?

Thanks,
Richard

---

### Post by Dex24 on 2009-02-09
I use example.org xxx.xxx.xxx.xxx.

---

### Post by Dex24 on 2009-02-09
Would my router have any play in this issue?

---

### Post by puppywhacker on 2009-02-09
The host file is only checked first if the nameswitch is set to do so (by default it is) Then you add in the hosts file the hostname and optionally  the hostname with full domain. In the resolv.conf you put the nameserver but also the search domain. so the hostname will be expanded to the full domainname

/etc/nsswitch.conf
hosts:          files dns

cat /etc/hosts
127.0.0.1	localhost
192.168.1.100	linksys	linksys.example.com

cat /etc/resolv.conf 
search example.com
nameserver 193.210.19.19

and your router no mostlikely doesn't play any role in your setup (it most likely a broadband switch and not a routing router)

---

