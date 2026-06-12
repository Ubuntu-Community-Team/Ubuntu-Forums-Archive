---
title: "Unable to Ping Websites in the Terminal"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by Zoot7 on 2009-04-12
Okay here's my story..

I'm running Ubuntu 8.04 and I connect to the net via a proxy, the address and port of which are 10.51.255.250 and 8080. A few weeks ago I discovered the keys for the Hardy Repository were outdated. I been trying to use the perl script in this thread:
**[http://ubuntuforums.org/showthread.php?t=1056099]("http://ubuntuforums.org/showthread.php?t=1056099")**
to update the keys for me, but it doesn't work because I'm behind a proxy it seems, and incidentally running ping from the terminal tells me the network is unreachable.

I've no problems with browsers, running apt-get or wget from the terminal, aps like skype or pidgin or even stuff like Flashget running under wine as regards connecting through that proxy. 

When I run the following:
```
http_proxy="http://10.51.255.250:8080/" ping -c 5 www.google.com
http_proxy="http://10.51.255.250:8080/" wget www.google.com -O /tmp/testgoogle
http_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad
https_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad2
```

Here's what I get:
```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" ping -c 5 www.google.com
connect: Network is unreachable
```

```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" wget www.google.com -O /tmp/testgoogle
--11:19:12--  http://www.google.com/
           => `/tmp/testgoogle'
Connecting to 10.51.255.250:8080... connected.
Proxy request sent, awaiting response... 302 Moved Temporarily
Location: http://www.google.ie/ [following]
--11:19:17--  http://www.google.ie/
           => `/tmp/testgoogle'
Connecting to 10.51.255.250:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 5,393         --.--K/s             

11:19:24 (2.41 MB/s) - `/tmp/testgoogle' saved [5393]
```

```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad
--11:20:13--  https://launchpad.net/~project-neon/+archive/ppa
           => `/tmp/testlaunchpad'
Resolving launchpad.net... 91.189.90.211
Connecting to launchpad.net|91.189.90.211|:443... failed: Network is unreachable.
```

```
mark@mark-laptop:~$ https_proxy="http://10.51.255.250:8080/" wget https://launchpad.net/~project-neon/+archive/ppa -O /tmp/testlaunchpad2
--11:20:58--  https://launchpad.net/~project-neon/+archive/ppa
           => `/tmp/testlaunchpad2'
Connecting to 10.51.255.250:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 49,813 (49K) [text/html]

100%[====================================>] 49,813       134.90K/s             

11:20:58 (134.75 KB/s) - `/tmp/testlaunchpad2' saved [49813/49813]
```

So, I'm wondering is there something wrong with the proxy settings, and if so how to fix it?

---

### Post by netztier on 2009-04-12
> **Zoot7 said:**
> 
```
mark@mark-laptop:~$ http_proxy="http://10.51.255.250:8080/" ping -c 5 www.google.com
connect: Network is unreachable
```


ICMP (the protocol used whith ping) can't use a HTTP proxy. The message "Network is unreachable" probably comes from a network router in your LAN that says: "sorry, I don't have any way to send a data packet to the IP address of www.google.com".

You could try to verify this with **traceroute**:
```
user@host:~$ **traceroute -n www.google.com**
```
You can expect to see error messages in the traceroute after a few hops - these will probably come from the same router that said "Network is unreachable" when you tried to ping [www.google.com](www.google.com).

Your proxy (10.51.255.250) however will know how to deal with a HTTP request - either by forwarding it to an upstream proxy or sending it to google.com. 

That's a common way to grant Internet access on a corporate network - the place where I work has a similar setup: the internal network (i.e. the routers) have no routing path towards the internet (i.e. no "default route"), all they know is the IP networks of the enterprise. Not even the "inner" HTTP proxies know how to get to the internet (speaking in terms of IP routing); they proxy-forward all requests (all *allowed* requests, that is) to the "outer" proxies in a DMZ on the firewall. Now these can send requests out to the internet, because the "outer" proxies, firewall and routers have the necessary routing information, either as "default routes" or as the full BGP internet routing table.

Such an approach might seem a bit complicated at first. But it comes to shine brightly when you have malware or worms breaking loose in your internal network; as long they are not proxy-aware (like the Conficker.B Worm was, around Jan 1st 2009), they can't update themselves via the Internet, and they can't be used as bots in a DDoS attack or start sending out spam messages, because there's just no way the can connect to any computer on the internet with a direct TCP connection.


regards

Marc

---

### Post by Zoot7 on 2009-04-12
Ah makes sense, thank you for the very detailed reply Marc. :)

Here's what I get with traceroute:
```
mark@mark-laptop:/etc/apt$ traceroute -n www.google.com
traceroute to www.google.com (66.102.9.147), 30 hops max, 40 byte packets
connect: Network is unreachable. 
```

---

### Post by netztier on 2009-04-12
> **Zoot7 said:**
> 
Here's what I get with traceroute:
```
mark@mark-laptop:/etc/apt$ traceroute -n www.google.com
traceroute to www.google.com (66.102.9.147), 30 hops max, 40 byte packets
connect: Network is unreachable. 
```

... er ... That's a bit less than I expected.

Can you show the outputs of **netstat -nr** , **ifconfig -a** and **arp -na** ?

regards

Marc

---

### Post by Zoot7 on 2009-04-12
> **netztier said:**
> ... er ... That's a bit less than I expected.

Can you show the outputs of **netstat -nr** , **ifconfig -a** and **arp -na** ?

Here's what I get:

```
mark@mark-laptop:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.51.0.0       0.0.0.0         255.255.0.0     U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
```

```
mark@mark-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:c5:86:5a:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190132 (185.6 KB)  TX bytes:190132 (185.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:46:76:17  
          inet addr:10.51.37.163  Bcast:10.51.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:e0ff:fe46:7617/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27107386 (25.8 MB)  TX bytes:3309574 (3.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-46-76-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
mark@mark-laptop:~$ arp -na
? (10.51.255.250) at 00:01:F4:05:1D:5C [ether] on wlan0
```

---

### Post by netztier on 2009-04-12
> **Zoot7 said:**
> Here's what I get:

```
mark@mark-laptop:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.51.0.0       0.0.0.0         255.255.0.0     U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
```


Ah. There we go. Your system does not have a default route. It only knows two networks: 10.51.0.0 (with mask 255.255.0.0, reachable over interface wlan0) and 169.254.0.0 (which is the auto-self-config-thingy-address as per RFC3330, which we can leave out of scope for this discussion).

So I was wrong: the "Network is unreachable" messages did *not* come from a router on your network after all, but from your local system itself. 

It can lookup google.com's IP addresss allright (that 66.102.9.147 address we saw), but when it consults it's routing table to see through which interface packets for 66.x.x.x should leave the system, there's no matching entry -> "Network is unrechable".

Strange ...

Is that some kind of special network you have there? How do you configure the IP settings for that network?
[LIST]
[*] in NetworkManager (automatic)?
[*] NetworkManager with a special profile with manual config? 
[*] via **/etc/network/interfaces**?
[/LIST]

Is there a DHCP server on it to dole out addresses? Could it be intentional that this DHCP server does *not* hand out information about a "default gateway"? DHCP servers normally do, and this information should lead to a default route entry in our routing table.

The default route would look something like this, where xx and yy would have to be some numbers between .0 and .255: 

```
user@host:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
...
0.0.0.0         10.51.xx.yy     0.0.0.0         UG        0 0          0 wlan0
...

```

OK, technically, we don't actually *need* a default route, just as long as we have a proxy server on that subnet where we can send our HTTP requests to, so that it can forward them on our behalf towards the Internet. Still, this makes for a somewhat unusual setup - the one I described in my earlier post does have default gateways for the client systems - it's a large network which has countless segments and subnets with numerous routers in between them, so we can't have all systems on a single subnet...

> 
```
mark@mark-laptop:~$ ifconfig -a
wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:46:76:17  
          inet addr:10.51.37.163  Bcast:10.51.255.255  Mask:[COLOR="Red"]255.255.0.0[/COLOR]
          inet6 addr: fe80::21d:e0ff:fe46:7617/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27107386 (25.8 MB)  TX bytes:3309574 (3.1 MB)
```

That's an awfully large subnet, especially for a subnet with WiFi clients. If that network gets used by more than a few dozen clients, performance will drop through the floor, should a little-more-than gentle broadcast or multicast storm^W breeze wash over it.

regards

Marc

---

### Post by Zoot7 on 2009-04-13
Again, thank you for the detailed reply Marc. :)

> **netztier said:**
> Is that some kind of special network you have there? How do you configure the IP settings for that network?
[LIST]
[*] in NetworkManager (automatic)?
[*] NetworkManager with a special profile with manual config? 
[*] via **/etc/network/interfaces**?
[/LIST]

Is there a DHCP server on it to dole out addresses? Could it be intentional that this DHCP server does *not* hand out information about a "default gateway"? DHCP servers normally do, and this information should lead to a default route entry in our routing table.
It's my college wireless network, whereby there are several access points throughout the campus.
Here are the settings:
```
**Authentication Type** 	WPA2 Enterprise with AES Encryption (more secure) or WPA Enterprise with TKIP Encryption(for older laptops)

**Security Key/Passpharese** 	Not Applicable

**EAP Type** 	PEAP/MS-CHAPv2

**Certificate **	Do not validate server certificates

**Proxy Auto Config(PAC)** 	Access to http and https (port 80 and 443 only).

**IP Address** 	Automatically assinged by DHCP 
```

---

### Post by netztier on 2009-04-14
> **Zoot7 said:**
> 
```

**Proxy Auto Config(PAC)** 	Access to http and https (port 80 and 443 only).

**IP Address** 	Automatically assinged by DHCP 
```

Okay - so there *is* DHCP on that network. *"port 80 and 443 only"* makes me think of "pretty restrictive internet access!" and so it does not come as a real surprise that the DHCP server doesn't seem to hand out information about a default gateway and the use of a proxy is mandatory.

So - from that network, you won't be able to use any service or protocol that does not support connecting over a HTTP/HTTPS proxy - which includes ICMP for the ping application.

Granted, there are ways to tunnel through proxies, but this needs closer investigation and a system under your control out on the internet.

regards

Marc

---

### Post by Zoot7 on 2009-04-15
Thanks for clearing that up for me. :)

---

