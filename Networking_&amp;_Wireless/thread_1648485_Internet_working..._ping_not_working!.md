---
title: "Internet working... ping not working?!"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by apocalypsemystic on 2010-12-18
So I have been browsing fine on my recently installed ubuntu 10.10 and I just discovered today that ping simply doesn't seem to be able to pick up anything but localhost. It just hangs. It should be pretty close to factory settings as I have not had the install for long. I have the same issue both on wireless and ethernet. I am running on a black 2007 macbook that triple boots with refit into snow leopard, vista, and ubuntu. Here are some printouts:

```
$ uname -a
Linux mycomputer 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux
``````
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:2a:23:1c:28:2f
          inet addr:138.16.28.39  Bcast:138.16.28.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe2f:9d1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5468385 (5.4 MB)  TX bytes:4588581 (4.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056 (1.0 KB)  TX bytes:1056 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:63:cc:ec:bd  
          inet6 addr: fe80::21b:63ff:fecc:ecbd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70049 (70.0 KB)  TX bytes:10079 (10.0 KB)
``````
$ ip rou
138.16.28.0/24 dev eth0  proto kernel  scope link  src 138.16.28.39  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 138.16.28.1 dev eth0  proto static
```[This thread]("http://ubuntuforums.org/showthread.php?t=1065764") has a similar problem but I'm not running a vm, and that's the closest I can find to what I'm experiencing.

If anyone has any thoughts, I am quite perplexed. Thanks.

---

### Post by capscrew on 2010-12-18
> **apocalypsemystic said:**
> So I have been browsing fine on my recently installed ubuntu 10.10 and I just discovered today that ping simply doesn't seem to be able to pick up anything but localhost. It just hangs. It should be pretty close to factory settings as I have not had the install for long. I have the same issue both on wireless and ethernet. I am running on a black 2007 macbook that triple boots with refit into snow leopard, vista, and ubuntu. Here are some printouts:

...


```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:2f:9d:1e  
          inet addr:**[COLOR="Red"]138.16.28.39[/COLOR]**  Bcast:138.16.28.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe2f:9d1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5468385 (5.4 MB)  TX bytes:4588581 (4.5 MB)
          Interrupt:16 

...


```

```
$ ip rou
138.16.28.0/24 dev eth0  proto kernel  scope link  src 138.16.28.39  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
**[COLOR="Blue"]default via 138.16.28.1 [/COLOR]**dev eth0  proto static
```

...

It appears that you are connected (see red above) through ```
resnet.brown.edu.
```
Specifically ```
39.28.16.138.in-addr.arpa. 3600	IN	PTR	youngorchard-39.resnet.brown.edu.
```

I'll bet that the network administrators have restricted your ability to ping the outside world.  Ping is the protocol: ICMP.  Browsing the web uses the protocols: HTTP or HTTPS.

Can you ping your default gateway (see blue above)?  That should be```
138.16.28.1
```

I can ping it.  See ```
>ping 138.16.28.1

Pinging 138.16.28.1 with 32 bytes of data:
Reply from 138.16.28.1: bytes=32 time=127ms TTL=241
Reply from 138.16.28.1: bytes=32 time=121ms TTL=241
Reply from 138.16.28.1: bytes=32 time=123ms TTL=241
Reply from 138.16.28.1: bytes=32 time=127ms TTL=241

Ping statistics for 138.16.28.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 121ms, Maximum = 127ms, Average = 124ms
```

---

### Post by Bucky Ball on 2010-12-18
Like capscrew says. Ping Google and you'll soon find out. It wouldn't be odd or unusual to be 'de-pinged' like this for security reasons:

```
ping google.com
```

If you get nothing, capscrew's on the money.

---

### Post by apocalypsemystic on 2010-12-18
Fair enough. I cannot ping that address. I suppose it's just disabled. Thanks.

---

### Post by Skripatch on 2010-12-21
Hello. I have the same problem. Ping is work properly in terminal but not in Ping Network Tools.

---

### Post by apocalypsemystic on 2010-12-21
My ping worked in neither terminal nor in the network tools. Now that I am on a different network ping works as expected. It sounds like it might be a different issue.

---

### Post by Bucky Ball on 2010-12-21
Or the same issue as ping probably would work on ***another network***.

---

### Post by bailewen on 2012-02-06
[deleted] 

Starting a new thread as requested. Didn't mean to jump on his issue. I thought since the orginal posters issue was solved . . .anyways:

Related issue here: [http://ubuntuforums.org/showthread.php?p=11669253#post11669253](http://ubuntuforums.org/showthread.php?p=11669253#post11669253)

Just shy about starting threads I guess.

---

### Post by Bucky Ball on 2012-02-06
> **bailewen said:**
> Been googling this issue for about an hour or so with no luck . . .

Here's a variation for you...I am online just fine but I can't even ping my own router (192.168.1.1)

I can ping 127.0.0.1 and I can ping my own address behind the router but nothign else, not even the other computer on my home network (Windows XP). The XP box, OTOH, can ping me just fine which makes me think I somehow disabled icmp. :confused:

ip rou gives me the following:

Maybe UFW is blocking it somehow? Like I said, I can access the internet just fine. I'm just playing around with my home network and trying to learn how to up security since my XP box is currently being hacked. (found the hacker through netstat but the linux box appears safe. . . for now) 

The weirdest thing of all is that if I put 192.168.1.1 into the browser address bar I still get the logon page but ping gets nothing. 

Any idea what's going on?

Please post a new thread with a descriptive title. This one's a year and a half almost old and well dead and buried. No-one will see you here and bad manners to jump on someone else's issue. ;)

Good luck. Post a link to your new thread here if you want.

---

