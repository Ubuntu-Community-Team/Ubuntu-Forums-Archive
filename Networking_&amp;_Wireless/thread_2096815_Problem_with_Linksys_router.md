---
title: "Problem with Linksys router"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by Brynwood on 2012-12-21
It's a long story.  Here goes:

I can't see any outside web pages using my Mythbuntu 12.04 machine, if I connect wirelessly to my sister's Linksys router. I get a solid connection, just no data. I can connect to my T-Mobile hotspot and surf the web, but it's much too slow.

When I connect to the linksys and go to 192.168.1.1, I can see the router's Linksys setup page.  I just can't go any further, either using a URL or an IP address (so, it's not a DNS problem.)  No pings work except to the router itself.

One exception: I have been able to surf the web using ubuntu and the linksys router, but only on the very first boot following a fresh install.  After that, nada.

Ready for the really weird part?  Using Windows, on the same machine or a different one, the linksys connection works fine. I can surf the web all day.  AND if I go to 192.168.1.1, I see a DIFFERENT router setup page!  It's similar to the linksys layout but different colors and branded SVEASOFT.  

I believe the ISP is this bunch: [http://www.mtpalomar.net]("http://www.mtpalomar.net") in Anza California.  

Any ideas what could be happening?

---

### Post by ahallubuntu on 2012-12-21
Is there a newer firmware available from Cisco for her particular router?  If so, I'd install it.  You of course (probably) have the option to install DD-WRT or Tomato firmware on her router, too.  That may solve your problem, even if you aren't completely sure what the problem was.

Is there an additional firewall enabled in the Linksys besides just the standard NAT firewall?  If so, try disabling it.

What's the Linksys connected to?  A DSL or cable modem?  Make sure it isn't also set to the same subnet as the Linksys (so not to 192.168.1.1/24).

---

### Post by fdrake on 2012-12-21
can you try to reboot the router? if still no luck post here the output for:
```

ifconfig
route -n
cat /etc/resolv.conf

```

---

### Post by Brynwood on 2012-12-21
> **ahallubuntu said:**
> Is there a newer firmware available from Cisco for her particular router?  If so, I'd install it.  You of course (probably) have the option to install DD-WRT or Tomato firmware on her router, too.  That may solve your problem, even if you aren't completely sure what the problem was.

Is there an additional firewall enabled in the Linksys besides just the standard NAT firewall?  If so, try disabling it.

What's the Linksys connected to?  A DSL or cable modem?  Make sure it isn't also set to the same subnet as the Linksys (so not to 192.168.1.1/24).

The router's not mine and I don't want to mess with it.  I'm a guest and I don't want to potentially brick the router.  FWIW, the firmware does have a 2005 date on it.

---

### Post by Brynwood on 2012-12-21
> **ahallubuntu said:**
> Is there a newer firmware available from Cisco for her particular router?  If so, I'd install it.  You of course (probably) have the option to install DD-WRT or Tomato firmware on her router, too.  That may solve your problem, even if you aren't completely sure what the problem was.

Is there an additional firewall enabled in the Linksys besides just the standard NAT firewall?  If so, try disabling it.

What's the Linksys connected to?  A DSL or cable modem?  Make sure it isn't also set to the same subnet as the Linksys (so not to 192.168.1.1/24).

And to your last question, it's connected to another linksys box (some kind of bridge I think) which has a coax cable leading to a yagi antenna on the house.

---

### Post by Brynwood on 2012-12-21
> **fdrake said:**
> can you try to reboot the router? if still no luck post here the output for:
```

ifconfig
route -n
cat /etc/resolv.conf

```

I rebooted it a few days ago with no effect.  Here's the output of those commands:
```
steve@steve-Latitude-E6400:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:bf:ef:02  
          inet addr:169.254.5.12  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:70ff:febf:ef02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8610387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:182274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11719207736 (11.7 GB)  TX bytes:20348585 (20.3 MB)
          Interrupt:22 Memory:f6fe0000-f7000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:758342 (758.3 KB)  TX bytes:758342 (758.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:21:f3:9a  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe21:f39a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:512462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:250629077 (250.6 MB)  TX bytes:29986035 (29.9 MB)

steve@steve-Latitude-E6400:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
steve@steve-Latitude-E6400:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```

---

### Post by |{urse on 2012-12-21
Just wanted to add that I have mint with working network on that specific laptop here, if you need any info (settings, conf files etc) for reference.

:popcorn:

---

### Post by Brynwood on 2012-12-30
> **|{urse said:**
> Just wanted to add that I have mint with working network on that specific laptop here, if you need any info (settings, conf files etc) for reference.

:popcorn:

Thanks for the offer.  

I think I have found a solution to the problem, though it doesn't make a lot of sense, considering the symptoms.

The router is about 100 feet away, so the signal is weak. A few feet away from my Linux laptop, I have a Windows Laptop with a Netgear WNA3100 USB wifi stick trying to talk to the same router.  I've discovered that if I unplug the Netgear stick from the Windows machine, my Linux laptop can now connect.  

My best guess:  The Netgear was "shouting" to make itself heard by the router, and interfering with the Intel wifi chip in my Linux box.  

It's definitely a headscratcher. :confused: I'll report if I find out an more.

---

