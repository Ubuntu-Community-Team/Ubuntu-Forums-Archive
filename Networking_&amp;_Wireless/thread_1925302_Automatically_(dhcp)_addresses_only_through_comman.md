---
title: "Automatically (dhcp) addresses only through command line"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by smilemukul on 2012-02-14
Hi,
I want to set automatically (dhcp) addresses only through command line for eth0 as Ubuntu default id "automatic dhcp" so that I can set DNS statically as per my requirement through CLI only & not through GUIin Ubuntu 11.04

Any solution will be appreciated

Thanks
mukul

---

### Post by raja.genupula on 2012-02-14
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by smilemukul on 2012-02-14
Thanks but i am customising my Ubuntu destop & require the info which is mentioned in the below url but only through CLI

Through GUI --->  Network Manager -> Wired -> Auto eth0 -> ipv4 Settings.

[http://askubuntu.com/questions/2321/what-is-the-proper-way-to-change-the-dns-ip/59153#59153](http://askubuntu.com/questions/2321/what-is-the-proper-way-to-change-the-dns-ip/59153#59153)

see option 5 in the above url.

Thanks
mukul

---

### Post by raja.genupula on 2012-02-15
> **smilemukul said:**
> Thanks but i am customising my Ubuntu destop & require the info which is mentioned in the below url but only through CLI

Through GUI --->  Network Manager -> Wired -> Auto eth0 -> ipv4 Settings.

[http://askubuntu.com/questions/2321/what-is-the-proper-way-to-change-the-dns-ip/59153#59153](http://askubuntu.com/questions/2321/what-is-the-proper-way-to-change-the-dns-ip/59153#59153)

see option 5 in the above url.

Thanks
mukul

ok i understand your issue . 

open your terminal and type 

```
sudo gedit resolv.conf 
```

type your DNS there . 

```
for example 
search XXX.XXX.XXX.XXX
nameserver XXX.XXX.XXX.XXX

```

hope that helps.

---

### Post by SeijiSensei on 2012-02-15
I you want to create a static resolv.conf that will persist through DHCP transactions, you need to edit the file /etc/dhcp3/dhclient.conf and remove the "domain-name", "domain-search" and "domain-name-servers" options from the "request" directive.  You can also use the "prepend" directive to override automatic lookups for these parameters.

---

### Post by smilemukul on 2012-02-16
Thanks but i want to set "Automatically (dhcp) addresses" permanently in GUI through CLI, there will be some configuration for  ipv4 Settings to be set through CLI so that it can be permanently viewed in GUI (Network Manager -> Wired -> Auto eth0 -> ipv4 Settings )

Thanks
mukul

---

### Post by smilemukul on 2012-02-16
How can I configure the below config in CLI & what will be the path,
[ipv4] method=auto dns-search=domain1.com;domain2.org;domain3.edu; ignore-auto-routes=false ignore-auto-dns=false

I hope now it will be clear that what i am trying to do.

Thanks.

---

