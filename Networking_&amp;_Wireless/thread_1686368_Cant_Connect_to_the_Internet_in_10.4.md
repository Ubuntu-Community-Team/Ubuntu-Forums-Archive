---
title: "Cant Connect to the Internet in 10.4"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by A. Ghofrani on 2011-02-12
Hi there,

I just re-installed my ubuntu 10.4, But I cant connect to the internet. 
Ubuntu **can** connect to my wireless; using ping command, I can see the ping and it seems fine. but i can not download any update or package and firefox cant show pages.

any idea?

---

### Post by A. Ghofrani on 2011-02-13
Bah, I re-installed again, this time i can easily update my ubuntu and even install new package using software center.
But still I have problem while using any Browser; I tried Firefox, Chromium & Arora, But no salvation...

A friend told me to add my Ifconig output to this post, so might help a bit...


[COLOR=DimGray][COLOR=DarkSlateGray]eth0      Link encap:Ethernet  HWaddr 00:1f:16:09:fb:50   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:28 Base address:0xc000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:425 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:260972 (260.9 KB)  TX bytes:260972 (260.9 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:99:83:10   
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:eaff:fe99:8310/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:100634 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:62577 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:128628883 (128.6 MB)  TX bytes:5694208 (5.6 MB)[/COLOR] [/COLOR]

would appriciate ur help...

---

### Post by mips on 2011-02-13
Check your DNS settings and try using public DNS servers like OpenDNS or Google.

Disable IPv6, many threads here on the topic if you need more info.

---

### Post by A. Ghofrani on 2011-02-14
TnX for ur reply, But I have disabled ipv6 [and it was on ignore as default]
I tried the wired network and it works fine, but when i use Wireless, only browsers r unable to work and they show the timeout message

---

### Post by A. Ghofrani on 2011-02-15
How to change dns settings?
Sorry but Im kinda noob on ubuntu...
 
can this be a result of something like firewall or something?

---

