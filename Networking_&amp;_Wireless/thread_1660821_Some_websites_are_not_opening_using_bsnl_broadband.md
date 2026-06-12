---
title: "Some websites are not opening using bsnl broadband"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by sougatain on 2011-01-05
Hi, I have got my bsnl broadband few weeks ago. It is running nicely on my ubuntu lucid desktop. But form past few days I'm unable to browse some of my websites from ubuntu. I have dual boot my pc wiht Microsoft Window XP(original). The websites which are not opening in ubuntu are easily opening in xp. I have changed the DNS servers to 8.8.8.8 and 8.8.4.4 and also my MTU to 1452 but nothing is happening. I called the customer care but they didn't gave me any fruitful solution. Please help me to overcome the problem. Thank you.

---

### Post by maverick555 on 2011-01-10
network connenction --> edit connection --> dsl --> edit then,go to ipv4 setting.
In method click manual -->then put address 192.168.1.3  netmask --> 255.255.255.0  gateway--> 192.168.1.1 
dns server--> 8.8.8.8,8.8.4.4 There is a quama , after 8.8.8.8
Click apply and restart your pc.

---

### Post by karthick87 on 2011-01-10
Have you tried another browser?And what website you are trying to access..If you are uisng firefox,then try clearing your browser caches and then try again..

---

### Post by sougatain on 2011-01-13
> **maverick555 said:**
> network connenction --> edit connection --> dsl --> edit then,go to ipv4 setting.
In method click manual -->then put address 192.168.1.3  netmask --> 255.255.255.0  gateway--> 192.168.1.1 
dns server--> 8.8.8.8,8.8.4.4 There is a quama , after 8.8.8.8
Click apply and restart your pc.
Thanks for your answer. I did exactly what you said. But its still not working. Most amazingly no information that I given is working. For making it easy for you I'm giving some screenshots and also output of my IFCONFIG. 

[[IMG]http://img407.imageshack.us/img407/2325/editingbsnl001.png[/IMG]]("http://img407.imageshack.us/i/editingbsnl001.png/")

[[IMG]http://img72.imageshack.us/img72/7002/connectioninformation00.png[/IMG]]("http://img72.imageshack.us/i/connectioninformation00.png/")


OUTPUT OF IFCONFIG
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:c9:f9:6f  
          inet6 addr: fe80::224:8cff:fec9:f96f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:214492 (214.4 KB)  TX bytes:157752 (157.7 KB)
          Interrupt:26 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.205.162.252  P-t-P:117.205.160.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:202681 (202.6 KB)  TX bytes:146367 (146.3 KB)

```

I am using the following modem:
[[IMG]http://img203.imageshack.us/img203/3010/34886024.jpg[/IMG]](http://img203.imageshack.us/i/34886024.jpg/)
But all is working in windows7 finely. 

PLEASE GIVE ME SOME FURTHER GUIDANCE.

---

### Post by karthick87 on 2011-01-13
Can you ping the ip address of the website?Post the output of,
```
ping 209.85.231.104
```

---

### Post by sougatain on 2011-01-14
> **karthick87 said:**
> Can you ping the ip address of the website?Post the output of,
```
ping 209.85.231.104
```
```
sougata@sougata-desktop:~/Desktop$ ping 209.85.231.104
PING 209.85.231.104 (209.85.231.104) 56(84) bytes of data.
64 bytes from 209.85.231.104: icmp_seq=1 ttl=53 time=117 ms
64 bytes from 209.85.231.104: icmp_seq=2 ttl=53 time=117 ms
64 bytes from 209.85.231.104: icmp_seq=3 ttl=53 time=116 ms
64 bytes from 209.85.231.104: icmp_seq=4 ttl=53 time=117 ms
64 bytes from 209.85.231.104: icmp_seq=5 ttl=53 time=117 ms
64 bytes from 209.85.231.104: icmp_seq=6 ttl=53 time=116 ms
64 bytes from 209.85.231.104: icmp_seq=7 ttl=53 time=116 ms
64 bytes from 209.85.231.104: icmp_seq=8 ttl=53 time=116 ms
64 bytes from 209.85.231.104: icmp_seq=9 ttl=53 time=116 ms
64 bytes from 209.85.231.104: icmp_seq=10 ttl=53 time=117 ms
64 bytes from 209.85.231.104: icmp_seq=11 ttl=53 time=116 ms
64 bytes from 209.85.231.104: icmp_seq=12 ttl=53 time=116 ms

```

---

### Post by sarim on 2011-01-14
Try disconnecting the connect again, then check if the configuration changes are working ?

---

### Post by sougatain on 2011-01-14
@sarim, I did everything new connection, disconnect and again connect, resetup also. But of them worked for me.

---

### Post by dineshs on 2011-01-14
If certain sites are not opening the problem might be MTU.Please refer[this]("http://ubuntuforums.org/showthread.php?t=872346") guide to find out the optimum value of MTU .Then set the value in Network manager via DSL tab or  see
[http://ubuntuforums.org/showthread.php?t=1619527](http://ubuntuforums.org/showthread.php?t=1619527)
Note :At present you are using *modem in Bridge mode*.You may try *modem in PPPoE mode* (Always ON mode where you dont need a PPPoE dialler to connect to internet) if the above method doesnt work.For this follow 
[http://www.calcutta.bsnl.co.in/dataoneinstall/mu12.html](http://www.calcutta.bsnl.co.in/dataoneinstall/mu12.html)

---

### Post by karthick87 on 2011-01-14
The problem is your DNS server i guess,Post the output of..

```
cat /etc/resolv.conf
```

---

### Post by albincepa on 2011-05-03
Hi i am new to ubuntu.
I am having the same problem here with my bsnl broadband connection.
I am now unable to open yahoo mail and some other websites in chrome and firefox. But these websites gets partially opened while viewed in the opera browser. But still not having satisfactory results.
pls help

---

### Post by dineshs on 2011-05-04
First [disable ipv6]("http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can") and see . If there is no luck please tell us what is the model name of your modem and how the connection is setup ie  bridge mode(using a dialler) or PPPoE mode (always ON)

---

### Post by albincepa on 2011-05-05
i tried disabling ipv6. But still no use.
I am using D-link Adsl 2+ router in bridge mode. I use dataone connection from bsnl.

---

### Post by dineshs on 2011-05-06
Since your modem is in bridge mode I think you are using [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9") method for connecting broadband.If yes please follow instructions [here]("http://ubuntuforums.org/showthread.php?t=1558579") to set a different MTU.(Disconnect and reconnect before you check)

---

### Post by prasannasp on 2011-09-12
I had the same problem. Now I have a solution for this. See my next reply.

---

### Post by prasannasp on 2011-09-13
> **sougatain said:**
> Hi, I have got my bsnl broadband few weeks ago. It is running nicely on my ubuntu lucid desktop. But form past few days I'm unable to browse some of my websites from ubuntu. I have dual boot my pc wiht Microsoft Window XP(original). The websites which are not opening in ubuntu are easily opening in xp. I have changed the DNS servers to 8.8.8.8 and 8.8.4.4 and also my MTU to 1452 but nothing is happening. I called the customer care but they didn't gave me any fruitful solution. Please help me to overcome the problem. Thank you.

Do not use that buggy Network Manager to set up a DSL connection. Use pppoeconf to setup a new connection.

```
sudo pppoeconf
```I had this same problem with my BSNL broadband too. I used to setup a new connection with NM. But I was not able to browse some sites like yahoo, facebook etc,. Then I configured my connection using pppoeconf. Now I can browse any site! I hope this could help you.. :)

-Prasanna SP

---

### Post by prasannasp on 2011-09-13
Use [this method]("https://help.ubuntu.com/community/ADSLPPPoE") to configure a new connection.
[URL="https://help.ubuntu.com/community/ADSLPPPoE"]
https://help.ubuntu.com/community/ADSLPPPoE[/URL]

---

### Post by jayamrutkar on 2011-12-30
I followed steps same steps as above but still have problems while loading sites like 
[http://in.bookmyshow.com](http://in.bookmyshow.com) or mainly [https://www.facebook.com](https://www.facebook.com)

Please help me out from this problem. :(

---

### Post by jayamrutkar on 2011-12-30
Oh my issue has been fixed after connections reset. Thanks a lot. :)

> **jayamrutkar said:**
> I followed steps same steps as above but still have problems while loading sites like 
[http://in.bookmyshow.com](http://in.bookmyshow.com) or mainly [https://www.facebook.com](https://www.facebook.com)

Please help me out from this problem. :(

---

### Post by kandukurivarun on 2012-10-31
> **karthick87 said:**
> Can you ping the ip address of the website?Post the output of,
```
ping 209.85.231.104
```

hi., even im also having the same problem...
the output of ping is

[I][B]PING 209.85.231.104 (209.85.231.104) 56(84) bytes of data.
^C
--- 209.85.231.104 ping statistics ---
15 packets transmitted, 0 received, 100% packet loss, time 14111ms[/B][/I]

can u guide me 4m here?

---

### Post by soham1996 on 2013-01-06
i am new to the linux community. I have installed 12.10 in my pc but i am unable to view some websites. I dont know why but they also load up very slow. I thought that linux was faster than windows. I am dual booting with windows 7 . Please help me! thnks

---

### Post by surajbanakar on 2013-07-12
This worked for me:
Delete the DSL Connection that you are using and create a new one. That's all !

---

### Post by DS_ED on 2014-04-15
> **prasannasp said:**
> Do not use that buggy Network Manager to set up a DSL connection. Use pppoeconf to setup a new connection.

```
sudo pppoeconf
```I had this same problem with my BSNL broadband too. I used to setup a new connection with NM. But I was not able to browse some sites like yahoo, facebook etc,. Then I configured my connection using pppoeconf. Now I can browse any site! I hope this could help you.. :)

-Prasanna SP

This was what solved it for me.

I'm using Xubuntu 13.10. And some sites were not at all loading. When I hit the site the broadband router lights would blink(indicating activity) for a few seconds and would stop. But the page would be endlessly loading.

Tried many different things, disabling ipv6, setting MTU, setting manually DNS servers. I guess the GUI networking tool to configure DSL connections is bugged.

Thanks Prasanna SP.

---

