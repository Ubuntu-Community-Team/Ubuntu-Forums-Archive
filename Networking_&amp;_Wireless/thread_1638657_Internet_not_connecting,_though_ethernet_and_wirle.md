---
title: "Internet not connecting, though ethernet and wirless connecting fine"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by sazhagianambi on 2010-12-05
Hello All,

  I am very much new to Linux, thought of posting in Absolute beginner how ever this could be right place as problem is much peculiar. 

  First let me brief the system details. I am using Sony Vaio VCF11 Series. Installed Ubuntu via WUBI. Upgraded to 10.10 64 bit and using for past few months. 

   My Internet is fine till today and suddenly now it stops working. As far as I know I didn't change any settings. When I tried both Wireless & ethernet system says connection established but firefox or any browser won't able to connect internet.  Even Sudo apt-get update tries to connect server and gives error as "some thing wicked happened". 

   I did checked on google and forums and found few forums but everything seems couple of years old and didn't help me much.   

  I already checked ipv6 settings and mode is ignore as suggested.....  As told it was working great for past few months till today...

please help me out.....forgive for making description is so long...   

Thank you.

Regards,
Nambi

---

### Post by dineshs on 2010-12-06
pl post result of```
ping -c3 4.2.2.1
```and```
route -n
```

---

### Post by sazhagianambi on 2010-12-06
Below is the details.....It sounds weird but this morning INTERNET seems to working as earlier....Though I tried restarting several times yesterday too..

nambi@ubuntu:~$ ping -c3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=53 time=27.1 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=53 time=26.7 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=53 time=26.4 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 26.420/26.782/27.143/0.295 ms


nambi@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


I have no clue as what happened earlier and now it got resolved.....:confused:...some explanation helps if there are..

Now I am posting this from Ubuntu....

Thank you for trying to help out....

---

### Post by grahammechanical on 2010-12-06
I do not know Wubi or how it works. My question is this: When you choose Ubuntu from the boot menu do you get a Ubuntu operating system that is directly interacting with the hardware? Or, is interacting through Windows? It may be that Windows is preventing Ubuntu from connecting to the Internet.

Another question: Can you alter Wubi settings? I wonder if it is possible to use Wubi to prevent Ubuntu from connecting to the Internet.

These are some of the things that I would investigate to find out why this happened.

Regards.

---

### Post by sazhagianambi on 2010-12-06
About Wubi, since its running as part of windows there is fair possibility hardware interacting thru windows...to be frank I don't understand it fully.......and I didn't change anything on Wubi other than default installation of 10.04 and upgrade them to 10.10.....

regardless I am glad internet working again....Thank you agian.

---

