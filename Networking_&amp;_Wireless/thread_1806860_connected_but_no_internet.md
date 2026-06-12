---
title: "connected but no internet"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by hkyork2064 on 2011-07-18
Hi
I upgraded my system to ubuntu 11.04 lately, everything works fine before but after upgrading to 11.04, firefox and chrome won't load any web pages. I use a adapter to connect to a router. I'm sure the network works fine as i can surf the web in windows using the same configuration. I have another device, which convert 3G cellular data to wifi network. In my city, the device refer to "pocket wifi"
If I connect ubuntu to the "pocket wifi", i everything works fine again.
any idea on how i can solve the problem?
what information do i have to put up here? 
Sorry for my poor presentation as i'm not a native speaker and i'm new to the linux family.
Thanks for you help!

---

### Post by poolet on 2011-07-18
open up a new terminal and type::

```
ping www.google.com
``````
ifconfig
```

and paste the output here....

---

### Post by hkyork2064 on 2011-07-18
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:8f:ed:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100624 (100.6 KB)  TX bytes:100624 (100.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:27:19:b2:b9:34  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:19ff:feb2:b934/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2875310 (2.8 MB)  TX bytes:672173 (672.1 KB)




PING [www.l.google.com](www.l.google.com) (74.125.71.104) 56(84) bytes of data.
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=1 ttl=55 time=20.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=2 ttl=55 time=20.7 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=3 ttl=55 time=19.2 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=4 ttl=55 time=19.8 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=5 ttl=55 time=20.4 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=6 ttl=55 time=20.6 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=7 ttl=55 time=22.1 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=8 ttl=55 time=21.5 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=10 ttl=55 time=20.9 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=11 ttl=55 time=22.9 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=12 ttl=55 time=205 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=13 ttl=55 time=21.6 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=14 ttl=55 time=19.4 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=15 ttl=55 time=20.2 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=16 ttl=55 time=112 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=17 ttl=55 time=28.1 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=18 ttl=55 time=19.6 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=19 ttl=55 time=23.5 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=20 ttl=55 time=156 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=21 ttl=55 time=43.5 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=22 ttl=55 time=286 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=23 ttl=55 time=71.9 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=24 ttl=55 time=225 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=25 ttl=55 time=155 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=26 ttl=55 time=26.0 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=27 ttl=55 time=18.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=28 ttl=55 time=21.9 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=29 ttl=55 time=24.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=30 ttl=55 time=121 ms
^N64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=31 ttl=55 time=19.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=32 ttl=55 time=21.7 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=33 ttl=55 time=20.1 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=34 ttl=55 time=19.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=35 ttl=55 time=21.7 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=36 ttl=55 time=19.2 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=37 ttl=55 time=22.7 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=38 ttl=55 time=18.8 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=39 ttl=55 time=19.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=40 ttl=55 time=24.8 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=41 ttl=55 time=19.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=42 ttl=55 time=18.4 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=43 ttl=55 time=24.5 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=44 ttl=55 time=18.9 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=45 ttl=55 time=19.8 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=46 ttl=55 time=20.3 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=47 ttl=55 time=20.0 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=48 ttl=55 time=174 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=49 ttl=55 time=20.7 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=50 ttl=55 time=19.5 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=51 ttl=55 time=22.9 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=52 ttl=55 time=27.6 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=53 ttl=55 time=24.4 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=54 ttl=55 time=26.7 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=55 ttl=55 time=20.8 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=56 ttl=55 time=158 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=57 ttl=55 time=20.1 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=58 ttl=55 time=20.2 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=59 ttl=55 time=20.0 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=60 ttl=55 time=20.0 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=61 ttl=55 time=20.4 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=62 ttl=55 time=20.0 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=63 ttl=55 time=20.8 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=64 ttl=55 time=460 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=65 ttl=55 time=187 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=66 ttl=55 time=187 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=67 ttl=55 time=200 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=68 ttl=55 time=190 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=69 ttl=55 time=157 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=70 ttl=55 time=173 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=71 ttl=55 time=191 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=72 ttl=55 time=326 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=73 ttl=55 time=336 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=74 ttl=55 time=169 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=75 ttl=55 time=179 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=76 ttl=55 time=207 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=77 ttl=55 time=168 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=78 ttl=55 time=157 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=79 ttl=55 time=170 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=80 ttl=55 time=149 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=81 ttl=55 time=19.2 ms
64 bytes from hx-in-f104.1e100.net (74.125.71.104): icmp_req=82 ttl=55 time=2720 ms



[COLOR="Red"]the ping command out seems will endless.[/COLOR] :(

---

### Post by poolet on 2011-07-18
go to your browser... Tools -> Preference

on the tab below got to advance and then network then connection settings and check if there is any proxy... Make sure that the "Use system proxy settings" is selected....


If the proxy settings are ok.... 

Try to uninstall and install again the fire fox or what ever is your browser.....

Hope that help you

---

### Post by hkyork2064 on 2011-07-19
i did exactly what you told me, it does not solve the problem :(

---

### Post by hkyork2064 on 2011-07-19
Bump :(

---

### Post by poolet on 2011-07-19
It's seems like your working fine. I really don't know what going wrong but for sure your problem is on the browser.. Try to uninstall and install it again to see what happen.... 

It's really strange since you can ping google.com and you get ip address.....

---

### Post by Duke.Augustine on 2011-07-19
> **hkyork2064 said:**
> Hi
I upgraded my system to ubuntu 11.04 lately, everything works fine before but after upgrading to 11.04, firefox and chrome won't load any web pages. I use a adapter to connect to a router. I'm sure the network works fine as i can surf the web in windows using the same configuration. I have another device, which convert 3G cellular data to wifi network. In my city, the device refer to "pocket wifi"
If I connect ubuntu to the "pocket wifi", i everything works fine again.
any idea on how i can solve the problem?
what information do i have to put up here? 
Sorry for my poor presentation as i'm not a native speaker and i'm new to the linux family.
Thanks for you help!
Are you sure that you want to get access to the Internet by wireless? Are you sure that the adapter is trying to connect to a wireless router?

If your adapter is connecting to an wireless router while actually it's an ethernet router, it will be failed.

---

### Post by jmoorse on 2011-07-19
First off, welcome.  It is good to see people from all over the world.

Ok, let's straighten this out:

1. Your pings worked because you were still connected to pocket wifi:
> 
wlan0 Link encap:Ethernet HWaddr 00:27:19:b2:b9:34 
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0

2. You have no IP address on your wired ethernet connection:
> 
eth0 Link encap:Ethernet HWaddr 00:1f:d0:8f:ed:47 
UP BROADCAST MULTICAST MTU:1500 Metric:1


**Please disconnect your pocket wifi when working on this.**  Otherwise we  won't be able to tell if our troubleshooting is helping.

Just to make sure we are on the same page:

Is your ethernet adapter plugged into your router?

Please post the output of:

```

sudo dhclient
sudo lspci -v

```

---

### Post by hkyork2064 on 2011-07-21
Thanks for all you help.
After days of researching, i conclude it is a hardware problem.
I'm using tp link wn821n for my wireless connection, which is known for having issue with linux.

---

