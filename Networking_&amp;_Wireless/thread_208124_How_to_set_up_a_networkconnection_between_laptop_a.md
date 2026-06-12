---
title: "How to: set up a network/connection between laptop and desktop?"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by Muiske on 2006-07-03
Hello all,


At home I have a desktop computer, which is my main working station. My girlfriend has a laptop with lots of data on it, and now I got the idea to transfer most of the laptop files to the desktop. I thought to hook up the laptop to the ADSL modem and then use SSH. That way, I am able to use SSH and internet at the same time (which, when I would plug in the ethernet cable to the other computer, would not give me this advantage). The problem is, I can't connect. 

The modem is a Thomson Speedtouch, which is connected to the internet through ADSL. It has 4 slots for computers to connect to. So far, when both the laptop and desktop have full access to the internet when they are connected to the modem. But SSH does not work when using the IP's given below - the password dialog opens, but when I enter the (correct!) password it still denies the access.

Using the command ifconfig on the desktop gives me this information:

```
eth0      Link encap:Ethernet  HWaddr 00:0E:A6:9E:13:93
          inet addr:10.0.0.150  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe9e:1393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:46430598 (44.2 MiB)  TX bytes:107990916 (102.9 MiB)
          Interrupt:185 Base address:0x9000

```

And on the laptop:

```
eth0      Link encap:Ethernet  HWaddr 00:02:44:74:CE:B8
          inet addr:10.0.0.152  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe74:ceb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24093036 (22.9 MiB)  TX bytes:35622736 (33.9 MiB)
          Interrupt:185 Base address:0x8000

```


To connect through SSH, I use the IP's given by ifconfig. However, according to my internet provider, my IP is 81.206.144.52 so the problem might be that I am using the wrong ones. I don't know how to find out what the REAL IP's are though. 

Am I totally stupid and doing something obviously wrong?

---

### Post by Muiske on 2006-07-03
Err.... nevermind. I figured it out - I am indeed stupid beyond redemption.







(I used the wrong username. :oops: )


Sorry for this!!

---

