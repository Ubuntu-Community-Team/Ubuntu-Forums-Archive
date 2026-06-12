---
title: "internet speed less than windows"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by apoorvmunshi on 2011-04-23
the dowloading speed i am getting is quite less than windows 7.
what can i do to improve speeed? i have DSL broadband connection....

---

### Post by Ropes on 2011-04-23
Oddly enough, I've noticed the same thing, it's probably my network settings which have become rather complicated lately, but programs like Jdownloader are roughly 50-75% the speed I was used to on Win7.  
I'm interested if there are any possible improvement hacks..

---

### Post by varunendra on 2011-04-23
Can we have some more details about your network setup? Like these:

[LIST]
[*]Are you using wired or wireless connection?
[*]Some insight in your modem/router's configuration if possible?
[*]Your connection speed (broadband package)
[*]Any specific figure about your nett or approx. download speed while downloading packages or ubuntu torrents (ubuntu iso torrents often max out the available download speeds)
[*]Any other detail you think important
[/LIST]
Plus outputs of (after browsing I-net a couple of minutes):
```
ifconfig
```
```
cat /etc/resolv.conf
```

I've seen sometimes the MTU values causing this issue due to packet loss, which can be verified from ifconfig command.

Interestingly, I personally have always experienced 10-15% gain in download speeds while using ubuntu! (while sometimes the 'page-opening' speed being slow, but download-speeds always faster than windows)

---

### Post by jonathan890 on 2011-04-25
> **apoorvmunshi said:**
> the dowloading speed i am getting is quite less than windows 7.
what can i do to improve speeed? i have DSL broadband connection....

Better you can install latest version of os like windows7 because there are many advanced features involved to speed up the internet, but if your computer's cofiguration does not support latest version, then you can install certain softwares that can speed up your internet and then you can check your net speed here [http://www.ip-details.com/internet-speed-test/](http://www.ip-details.com/internet-speed-test/)

---

### Post by kmcbest on 2011-07-26
Exactly the same thing here. Tested with this site
[http://test-debit.free.fr/](http://test-debit.free.fr/)
to download the file "image.iso".

@Win7: 1.9MB/s
@Ubuntu 11.04: 750KB/s

That's >50% slower, I really wonder why....
```
kmc@kmc-System-Product-Name:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:08:56:09  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe08:5609/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7394279 (7.3 MB)  TX bytes:2855144 (2.8 MB)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)


```

---

### Post by varunendra on 2011-07-27
Try disabling IPv6 using this guide: [http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
or this one: [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

