---
title: "Internet connection not working in KUBUNTU"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by ramnathnagappan on 2009-02-16
I am able to use Internet in from the XP boot but not from the Kubuntu. My XP configurations look like this.....---->

INTERNET Protocl(TCP/IP) Properties
<Use  the following IP address>
IP Adress:      10.201.200.12
Subnet Mask:    255.0.0.0
Default Gateway: . . . 

<Use  the following DNS server address>
Prefered DNS Server : 10.201.239.89

In browser-->Proxy settings--->Internet properties--->LAN settings
<Use a proxy server for LAN is checked true>
Address :10.201.239.90
Port: 8080
(Bypass proxy server for local address is Checked true)
(Advanced)Proxy settings-->
Http : 10.201.239.90(Using same for all protocols)

I have almost configured the same in Kubuntu in Network manager by adding new wired connection and proxy settings in my Konqueror browser .... But all in vain!!!
Plz suggest me some a solution

---

### Post by ramnathnagappan on 2009-02-23
sOME ONE REPLY PLZ...

---

### Post by Iowan on 2009-02-23
Post results of **ifconfig** and contents of */etc/network/interfaces*. Is the connection working on local network (**ping**'s work, etc)?  I haven't dealt with proxy servers before, but I can at least give your thread a bump...

---

