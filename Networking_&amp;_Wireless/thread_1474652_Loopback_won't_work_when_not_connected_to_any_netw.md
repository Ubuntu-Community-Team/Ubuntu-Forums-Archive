---
title: "Loopback won't work when not connected to any network"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by sratostat on 2010-05-06
Good day to everybody.

I'm using Wordpress on Apache localy to keep a diary (it's convenient because of the tags). 
When I'm connected to any network (be it wired or wireless) my Apache (and Wordpress, of course) works just fine. But as soon as I go offline, I can't access the web server neither through browser nor by telneting to the 80th port. 
Pinging localhost works just fine.

Here is my ifconfig when offline and when online:

Online:
```
eth0      Link encap:Ethernet  HWaddr 00:24:54:6f:07:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2995483 (2.9 MB)  TX bytes:2995483 (2.9 MB)

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:6f:07:87  
          inet addr:192.168.1.118  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f27b:cbff:fe6f:787/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28070593 (28.0 MB)  TX bytes:4854448 (4.8 MB)

```

Offline:


```
eth0      Link encap:Ethernet  HWaddr 00:24:54:6f:07:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3001943 (3.0 MB)  TX bytes:3001943 (3.0 MB)

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:6f:07:87  
          inet6 addr: fe80::f27b:cbff:fe6f:787/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28142321 (28.1 MB)  TX bytes:4867453 (4.8 MB)

```

And here is nmap listing.

Online:


```
root@V:/home/v# nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-05-06 17:21 MSD
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 996 closed ports
PORT      STATE SERVICE
80/tcp    open  http
631/tcp   open  ipp
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.51 seconds

```

Offline:


```
root@V:/home/v# nmap localhost

Starting Nmap 5.00 ( http://nmap.org ) at 2010-05-06 17:23 MSD
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
mass_dns: warning: Unable to determine any DNS servers. Reverse DNS is disabled. Try using --system-dns or specify valid servers with --dns-servers
Interesting ports on localhost (127.0.0.1):
Not shown: 996 closed ports
PORT      STATE SERVICE
80/tcp    open  http
631/tcp   open  ipp
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.39 seconds

```

Is the routing? Maybe I should manually create a route to localhost while offline?

P.S. As you all can see, i'm using webmin on 10000th port. When offline it's unavailable as well.

Thanks alot.

---

### Post by myk.dinis on 2010-05-06
Is apache set to respond when it doesn't detect an active network connection?

Also, what's the metric for lo?
lo should have the lowest possible metric...

cheers!

-myk

---

### Post by sratostat on 2010-05-06
Thanks for your reply!

The metrix is the same on all of the interfaces -- 1.
Regarding changin Apache's settings: how do you do that? Where can I set it up to work even with no connection?

Anyway, in my opinion, it's not Apache's fault, because Webmin, which uses web-interface as well, doesn't work when offline also.

Weird business =)

---

### Post by myk.dinis on 2010-05-06
Remember, lo ***needs*** to have a metric of 1. No other adapters should.

:)

-myk

---

### Post by sratostat on 2010-05-06
Thank you for your time.

The issue was in my browsers: both firefox and chrome used their own network settings and didn't changed them when I went offline. 
I managed to resolve the issue only in firefox, where I swithced network connection to direct from automatic proxy detection. 
The same action if chrome solved nothing: it's a smartass piece of software that tries to do stuff for you sometimes against your will =)

---

### Post by Iowan on 2010-05-06
> **sratostat said:**
> 
The same action if chrome solved nothing: it's a smart*** piece of software that tries to do stuff for you sometimes against your will =)Hmmm... more software that (thinks it) knows what you want better than you do. :roll:

---

### Post by aihua on 2010-06-20
Hi,

When you **not connected to any network**, firefox will **work** itself **offline**, please uncheck it from "**File**"->"**Work Offline**", then you can access localhost or 127.0.0.1 even if you **not connected to any network. **Maybe it is same with Chrome. I have no Chrome, please try it.

---

### Post by sratostat on 2010-06-21
> **aihua said:**
> Hi,

When you **not connected to any network**, firefox will **work** itself **offline**, please uncheck it from "**File**"->"**Work Offline**", then you can access localhost or 127.0.0.1 even if you **not connected to any network. **Maybe it is same with Chrome. I have no Chrome, please try it.

Hello.
You're absolutely right, Firefox works that way. My bad, I didn't mention it earlier.
In Chrome I haven't found any corresponding option.
Chrome moves in mysterious ways: steals alot of CPU and doesn't let you fiddle with its intestines.

---

