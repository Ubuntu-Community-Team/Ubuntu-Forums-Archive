---
title: "Ubuntu 11.10 on laptop won't connect to ethernet"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by ScorchingFalcon on 2012-03-15
Hi, I'm dual-booting ubuntu 11.10 with windows 7 and my ethernet connection works fine with windows but won't seem to work with ubuntu. I've been searching through google for troubleshooting help and have been following what the guy with similar problem in this thread ([http://ubuntuforums.org/showthread.php?t=1802235](http://ubuntuforums.org/showthread.php?t=1802235)) did but after a while my outputs started to differ from his so I'm at a loss here (sorry, I'm a newbie in this kinda thing). 

I have a hunch I'm missing firmwares or there's something funny going on as eth1 (the connection I'm apparently using) says no link in the messages but eth0 has some outputs.

The outputs for the commands as ran in my laptop is attached.

Can anybody help me? Thank you in advance.

---

### Post by matt_symes on 2012-03-15
Hi

Your interface is down and disabled.

```
sudo ifconfig eth0 up
```

Does that help ?

Kind regards

---

### Post by ScorchingFalcon on 2012-03-15
This is what I got :S

> 
$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device


---

### Post by ScorchingFalcon on 2012-03-16
so... any idea?

---

### Post by winh8r on 2012-03-16
You need to use 

```
sudo ifconfig eth1 up
```

your device is seen on eth1 according to your posted info.

try the above to get it started.

if you find it is slow and lagging compared to Windows then have a look here [http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/]("http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/")
for a resolution to a realtek driver issue, just follow the steps given.

Note down what you do in case you need to go back and alter anything though.

Any questions just ask.

Hope this helps

---

### Post by ScorchingFalcon on 2012-03-16
when I used "sudo ifconfig eth1 up" like you instructed there's no output from the terminal and my laptop still won't connect to the ethernet connection :S

---

### Post by winh8r on 2012-03-16
run 

```
ifconfig
```

in the terminal and post it in your reply please.

---

### Post by ScorchingFalcon on 2012-03-17
Here you go:

```
~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 54:04:a6:2f:dd:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr e0:b9:a5:67:07:bf  
          inet addr:172.17.36.26  Bcast:172.17.63.255  Mask:255.255.192.0
          inet6 addr: fe80::e2b9:a5ff:fe67:7bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16218298 (16.2 MB)  TX bytes:1399808 (1.3 MB)


```

---

