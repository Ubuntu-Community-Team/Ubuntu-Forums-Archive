---
title: "Forwarding"
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by Ane Lenstra on 2012-10-03
I got a desktop-server with 2 network interfaces. eth0 and eth1.

eth0: connected to internet, IP 10.112.76.22 DNS 10.100.102.73 and .74
eth1: connected local, IP 192.168.1.21 DNS 10.112.76.22 (eth0)

I want to forward internet connection from eth0 to eth1. Which commands do I need to do this? And is my DNS the right 1?

---

### Post by cway00 on 2012-10-03
Based on your information [
QUOTE=Ane Lenstra;12275202]I got a desktop-server with 2 network interfaces. eth0 and eth1.

eth0: connected to internet, IP 10.112.76.22 DNS 10.100.102.73 and .74
eth1: connected local, IP 192.168.1.21 DNS 10.112.76.22 (eth0)

I want to forward internet connection from eth0 to eth1. Which commands do I need to do this? And is my DNS the right 1?[/QUOTE]

Try the following from the link as stated below link
 ```

http://rbgeek.wordpress.com/2012/04/29/how-to-install-the-dhcp-server-on-ubuntu-12-04lts/

```

---

### Post by SeijiSensei on 2012-10-03
I think you're asking how to make machines with addresses in the 192.168 space be able to see the Internet, yes?

You do this with something called "network address translation" or "IP masquerading."  Read this:

[https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29)

By the way, the bolded comment in that article that turning off IP forwarding since Hardy is a "bug" is not correct.  It is a security precaution.  Most all modern distributions now disable IP forwarding by default.

---

### Post by Ane Lenstra on 2012-10-03
> **cway00 said:**
> Based on your information
 
Try the following from the link as stated below link
```

http://rbgeek.wordpress.com/2012/04/29/how-to-install-the-dhcp-server-on-ubuntu-12-04lts/

```
 
Thanks.
 
I've got a FOG server installed which uses DHCP to give IP-addresses. Followed this tutorial but it still won't work.
 
Isn't there something I need to configurate with IPTABLES?

---

