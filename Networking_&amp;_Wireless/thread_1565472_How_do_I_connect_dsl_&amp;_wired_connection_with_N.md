---
title: "How do I connect dsl &amp; wired connection with NM?"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by DavidYun on 2010-09-01
Hello Everyone:

  The situation is I have one machine just installed 10.04

yesterday, and I plan to take it as FTP server sharing files

via LAN and WAN as well. But after setting up all network with

Network-Manager, I found that [COLOR=Red]my dsl connection will

disconnect while my wired connection was connected.[/COLOR]

my network-manager setting process is:
  1.wired tab:
     IPv4:192.168.1.x
     Mask:255.255.255.0
     GW:192.168.1.1
  2.DSL tab:
     enter the username and password that my ISP gave me.

==

after my googling

I fix it with pppoeconf and edit the /etc/network/interfaces

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
address 192.168.1.17
gateway 192.168.1.1
netmask 255.255.255.0

==

Because my Ubuntu server has normal user(don't know how 

to use Terminal), I want to get all setting done with mouse 

clicking by using the default applet.

So, does anybody know how to setup LAN and DSL connection

via Network-Manager only to let them connect at the same 

time?

---

### Post by Iowan on 2010-09-01
From Code of Conduct:> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post. 
Fixed it for you. :)

---

### Post by DavidYun on 2010-09-02
Thanks Iowan, But can anybody answer my question?

---

