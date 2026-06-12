---
title: "DNS problem?? i cant see intranet site anymore"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by gadgetguru on 2009-12-19
Hi Guys hope you can help.
I run kubuntu 9.10 local machine.
I have an ubunu 8.10 server on network 192.168.2.200
server has lamp installed and running smoothly.
It hosts a web site my-intranet-site.net which is available nw wide and wifi wide.
I have installed and configured DNS on server machine.
Now i have installed LAMP on local machine and since this install   when i try to access [http://my-intranet-site.net](http://my-intranet-site.net), from my local machine in any browser, instead of my ubuntu server hosted website, it get the message back "It works" just as if i had typed localhost or 127.0.0.1??? If I type the ip address it works fine. 
Odd as I have not configured apache. it is as just installed. type any other fictitious address and it is not found as you would expect.
My colleague runs xp with wamp he has no problems connecting to my-intranet-site.net

If i ping 192.168.2.200 ..replies no problems
traceroute reports jut one hop to destination all good..??
any help would be greatly appreciated... I have already un-installed local lamp several times, on local machine and now have a complete rebuild with same result!!! 

Pls let me know if you need any further info.

---

### Post by Iowan on 2009-12-20
Kubuntu machine having any problems accessing other sites (is it using the DNS server)?

---

### Post by gadgetguru on 2009-12-22
Thanks Iowan ,
No problems with any other sites. DNS ctually seems fine. I Have retitled APACHE problem?
Having disconnected from my network and tried again, it still resolved and displayed "It Works!" as before...so must be apache problem? I cant figure it. I had not configured Apache in any way, just installed it.

---

