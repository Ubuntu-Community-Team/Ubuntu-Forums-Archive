---
title: "ubuntu 10.04/11.10 64 bit wired internet problem"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by galapah on 2012-04-23
Hi,

I have installed Ubuntu 11.10 and later 10.04 on my laptop where both wired and wifi connection on Windows were working without any problem.

Now I am lost. The connection is not working. (Let's consider now only the wired one; wifi will be more difficult to set up).

**What IS working:**
* the OS says the device is connected to the network
* I can reach SOME websites in the browser: google.com, wikipedia.org, bbc.co.uk, youtube.com etc.
+ domain names are translated correctly into IP addresses

**What IS NOT working:**
* other websites
** ping to any address (including those that I can open in the browser) -- it has 100% loss. (The same is true for other computers in the network where the connection is allright.)*
* software repositories - I cannot connect to them so I cannot install anything

I tried to use Google Public DNS server but it did not help.

Here is what I get with ifconfig and netstat:
```
jan@arthur:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr XXXX  
          inet addr:XXXX  Bcast:XXXX  Mask:255.255.252.0
          inet6 addr: XXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1043511 (1.0 MB)  TX bytes:178177 (178.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6496 (6.4 KB)  TX bytes:6496 (6.4 KB)

wlan0     Link encap:Ethernet  HWaddr XXXX 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jan@arthur:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
XXXX    0.0.0.0         255.255.252.0   U         0 0          0 eth0
XXXX     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         XXXX    0.0.0.0         UG        0 0          0 eth0
```Any suggestions are welcome!

---

### Post by kc1di on 2012-04-23
just a question does you router have any kind of firewall enabled?

If so you may want to try to disable it for a test and see if that is the problem.

---

### Post by galapah on 2012-04-23
Hi,
thanks for suggestion but I am connecting to the university router so I do not have control over it.
J.

---

### Post by galapah on 2012-04-23
I have moved to another place. I do not have LAN connection here but wifi works fine here. So the problem is only with the LAN connection.

---

### Post by kc1di on 2012-04-23
> **galapah said:**
> I have moved to another place. I do not have LAN connection here but wifi works fine here. So the problem is only with the LAN connection.
Check with the University IT chief maybe there is something that needs to be entered.

---

### Post by galapah on 2012-04-23
Definitely not. As I wrote in my first post, it worked on Windows...

Tomorrow, I will install Ubuntu 12.04 although it is not the official release yet. But I do not believe much it will help.

> **kc1di said:**
> Check with the University IT chief maybe there is something that needs to be entered.

---

### Post by galapah on 2012-04-24
I have tried also 11.10 32bit and 12.04 Beta2 32bit -- without success...
BTW, ping does not work even on other computers in the network.

---

### Post by galapah on 2012-04-25
Nobody has any idea? :/

Still not working. But now I have used a LAN cable from a Win computer where the connection is ok and plugged it into my Ubuntu and the result is the same (So it clearly is not a problem of the cable or IP address.).

I also tried connecting the two computers: Win-Linux. Connection ok (both machines say the connection is established), ping from the windows ok, ping from Ubuntu fails!

I have no idea... The only thing which comes to my mind is that it is a problem of the driver. But I googled my type (NetXtreme BCM5753M) and could not find any complaints, just the opposite, it should operate in Linux. Kernel driver in use is tg3.

---

### Post by galapah on 2012-04-29
Well, I was sure that it did not have anything to do with the network because the connection was working on Windows. Yet I have gone to the computer dpt. today and the problem is solved!

I needed to set proxy; strange I do not remember I had set it on Windows.

---

