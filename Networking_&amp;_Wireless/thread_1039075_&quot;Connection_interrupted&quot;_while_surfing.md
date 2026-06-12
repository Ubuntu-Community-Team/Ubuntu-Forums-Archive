---
title: "&quot;Connection interrupted&quot; while surfing"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by gMinuses on 2009-01-14
While surfing on Internet, I keep getting this "connection interrupted" message from Firefox all the time.
It can happen to any website, e.g. google.com, ubuntu.com ,etc , and occur randomly. Sometimes everything is normal, sometimes I have to "try again"(reload) like a million times to load the web.

The problem seem to be my router(TP-Link WR340G). Because if I bypass the router and use PPPoE directly, everything is fine, and if I switch back, the message comes back as well.
One thing is also strange. I have XP installed at the same time. When booting to XP, the problem is gone(also using Firefox), and if I use Virtualbox on my XP, and install ubuntu in it , there is no problem either. I don't have any firewall(including the default one) or AV software installed on XP.

I have tried to disable ipv6 in Firefox and Ubuntu, and is still not working. [it seems that some people is experiencing this issue too]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/298128").

So do you guys have any idea?
Any kind of help will be appreciated.

---

### Post by superprash2003 on 2009-01-14
try changing dns servers to opendns - 208.67.222.222 and 208.67.220.220
For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

if you still face problems, post output of ifconfig from the terminal

---

### Post by gMinuses on 2009-01-14
Changing dns server doesn't work, still get this message.
Here is the output:
```
eth0      Link encap:Ethernet  HWaddr 00:0d:87:a0:56:34  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:5215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1898071 (1.8 MB)  TX bytes:487320 (487.3 KB)
          Interrupt:23 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

```

---

### Post by gMinuses on 2009-01-15
help please.

---

### Post by superprash2003 on 2009-01-15
ok.. im almost sure its an MTU issue, cause your mtu is 576 which is pretty low.. try changing your mtu value [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by gMinuses on 2009-01-15
Wow! You are absolutely right. It is the MTU. After setting it to 1492, everything went normal. 
You are the hero, man. I'm gonna post this thread link to launchpad.
Thanks a lot!

---

### Post by gMinuses on 2009-01-15
But is it a ubuntu bug? The MTU was "automatic" before, and it should have worked.
You don't have to set MTU manually in XP.

---

### Post by superprash2003 on 2009-01-18
is this 8.10 ?? if so i think it is.. many users have reported this problem in the forums..

---

### Post by trigoman05 on 2010-05-02
> **superprash2003 said:**
> try changing dns servers to opendns - 208.67.222.222 and 208.67.220.220
For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

if you still face problems, post output of ifconfig from the terminal

Thank you! Changing to opendns servers solved my problem! :D

---

### Post by bharahb on 2010-05-29
Had the same problem. Changing to openDNS solved it!!
Thanks a lot!! :)

---

