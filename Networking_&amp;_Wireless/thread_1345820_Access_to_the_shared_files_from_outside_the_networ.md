---
title: "Access to the shared files from outside the network"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Meelad on 2009-12-04
**System:** Ubuntu 9.10 with Samba installed.

**Details:** I have an ubuntu 9.10 server installed with samba to share files and folders inside an internal network, and it works like a charm.

What I need is access to those files and folders (with the same rights) from outside the network (i.e. through the internet). How can I do that?

**Already tried:**
- I have already done it with FTP, but the problem with that is that it doesn't allow me to edit the files directly on the server (since it's only a file transfer protocol). What I need is direct access, as if you are sitting inside the network.. What's the easiest (free) way to do it?

Any help will be MUCH appreciated..

---

### Post by sanderj on 2009-12-04
To **me**, samba access over **ipv6** is most easy; no NAT problems involved.

See [http://ipv6-or-no-ipv6.blogspot.com/2008/12/samba-windows-share-over-ipv6.html](http://ipv6-or-no-ipv6.blogspot.com/2008/12/samba-windows-share-over-ipv6.html)

For Samba over IPv6, you will need ... IPv6. It's quite harmless to "sudo apt-get install miredo" and then see whether you get a 2001: address, and can "ping6 ipv6.google.com".


```
sander@quirinius:~$ ping6 ipv6.google.com
PING ipv6.google.com(fx-in-x68.1e100.net) 56 data bytes
64 bytes from fx-in-x68.1e100.net: icmp_seq=1 ttl=56 time=42.4 ms
64 bytes from fx-in-x68.1e100.net: icmp_seq=2 ttl=56 time=38.2 ms
64 bytes from fx-in-x68.1e100.net: icmp_seq=3 ttl=56 time=37.9 ms
64 bytes from fx-in-x68.1e100.net: icmp_seq=4 ttl=56 time=38.4 ms
^C
--- ipv6.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3007ms
rtt min/avg/max/mdev = 37.974/39.265/42.417/1.833 ms
sander@quirinius:~$ 

```

---

### Post by DGortze380 on 2009-12-04
> **meelad said:**
> **system:** ubuntu 9.10 with samba installed.

**details:** i have an ubuntu 9.10 server installed with samba to share files and folders inside an internal network, and it works like a charm.

What i need is access to those files and folders (with the same rights) from outside the network (i.e. Through the internet). How can i do that?

**already tried:**
- i have already done it with ftp, but the problem with that is that it doesn't allow me to edit the files directly on the server (since it's only a file transfer protocol). What i need is direct access, as if you are sitting inside the network.. What's the easiest (free) way to do it?

Any help will be much appreciated..

vpn

---

### Post by Meelad on 2009-12-04
Thanks for the replies.

sanderj, the problem with IPv6 is that it is not compatible with all hardware, and that could very well be a problem for me trying to set up the network in 6 different locations.

And DGortze380, is vpn free? I saw you have to purchase some licenses to use it, is there a free vpn way to use?

---

### Post by DGortze380 on 2009-12-04
> **Meelad said:**
> Thanks for the replies.

sanderj, the problem with IPv6 is that it is not compatible with all hardware, and that could very well be a problem for me trying to set up the network in 6 different locations.

And DGortze380, is vpn free? I saw you have to purchase some licenses to use it, is there a free vpn way to use?


[http://www.openvpn.net/](http://www.openvpn.net/)

---

