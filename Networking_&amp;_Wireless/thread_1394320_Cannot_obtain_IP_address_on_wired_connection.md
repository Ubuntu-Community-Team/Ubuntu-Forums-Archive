---
title: "Cannot obtain IP address on wired connection"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by jgb2185 on 2010-01-30
I am having a persistent problem with getting a wired network connection under a recent install of Ubuntu 9.10. The network manager will show the wired network as 'disconnected' after a restart. This is true whether I am connected directly to my ISP's modem, or through the Linksys router that I usually use.

The output of **ifconfig** suggests that eth0 is not being assigned an IP address:

```
eth0      Link encap:Ethernet  HWaddr 00:30:1b:ac:5b:9e  
          inet6 addr: fe80::230:1bff:feac:5b9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9408 (9.4 KB)  TX bytes:9408 (9.4 KB)
```

Running **dhclient** seems to confirm this:

```
Listening on LPF/eth0/00:30:1b:ac:5b:9e
Sending on   LPF/eth0/00:30:1b:ac:5b:9e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Following some research on these forums, I made the following changes to **dhclient.conf**:

```
# commented out 
# option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

# added
send vendor-class-identifier "MSFT 5.0";

# removed rfc3442 reference
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu,
	ntp-servers;
```

This has no effect on the problem.

I have reached the limits of my own ingenuity. Can anyone suggest additional fixes?

Thanks...

JGB

---

### Post by Barriehie on 2010-01-30
What happends when you:
```

ifup eth0

```

Barrie

---

### Post by jgb2185 on 2010-01-30
Running

```

sudo ifup eth0

```

gives the result

```

Ignoring unknown interface eth0=eth0

```
**eth0** is not defined in **/etc/network/interfaces**. This is the norm, is it not?

---

### Post by Barriehie on 2010-01-30
> **jgb2185 said:**
> Running

```

sudo ifup eth0

```

gives the result

```

Ignoring unknown interface eth0=eth0

```
**eth0** is not defined in **/etc/network/interfaces**. This is the norm, is it not?

Not on this machine!

[color="green"]**/etc/network/interfaces**[/color]
```

auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.using
  post-down iptables-save -c > /etc/iptables.using

```

What does your /etc/network/interfaces file look like?

Barrie

---

### Post by pillu on 2010-01-30
I am having the exact same problem with my 9.10 install when I connect to my office wired LAN. I will be watching this thread too. Also, when I add the eth0 entries in /etc/network/interfaces, network manager then refuses to manage eth0. I think these entries might have been removed from /etc/network/interfaces in newer Ubuntu versions.

---

### Post by Barriehie on 2010-01-30
> **pillu said:**
> I am having the exact same problem with my 9.10 install when I connect to my office wired LAN. I will be watching this thread too. Also, when I add the eth0 entries in /etc/network/interfaces, network manager then refuses to manage eth0. I think these entries might have been removed from /etc/network/interfaces in newer Ubuntu versions.

The joys of upgrading... 8)

---

### Post by jgb2185 on 2010-01-30
Contents of **/etc/network/interfaces**:

```

auto lo
iface lo inet loopback

```

If I understand correctly, any interface listed in **/etc/network/interfaces** will not be managed by Network Manager.

In the interim, I have tried booting from several live CDs I have on hand, including Ubuntu 9.10, Knoppix 5.1, Linux Mint 4, and even an old UBCD4WIN (a live CD version of Windows XP). None of these were able to obtain a DHCP address.

---

### Post by Barriehie on 2010-01-30
> **jgb2185 said:**
> Contents of **/etc/network/interfaces**:

```

auto lo
iface lo inet loopback

```

If I understand correctly, any interface listed in **/etc/network/interfaces** will not be managed by Network Manager.
Don't know about that.

> **jgb2185 said:**
> 
In the interim, I have tried booting from several live CDs I have on hand, including Ubuntu 9.10, Knoppix 5.1, Linux Mint 4, and even an old UBCD4WIN (a live CD version of Windows XP). None of these were able to obtain a DHCP address.

Have you tried completely shutting the machine down and then turn it back on? i.e. a cold boot?

---

### Post by Iowan on 2010-01-30
> **jgb2185 said:**
> If I understand correctly, any interface listed in **/etc/network/interfaces** will not be managed by Network Manager.
That's the way it's *supposed* to work - although there's an option (somewhere?) to change "managed" from "false" to "true". I haven't tried it...

---

### Post by jgb2185 on 2010-01-30
I have resolved this issue. I began to think that the problem lay with Network Manager, so I first added these lines to **/etc/network/interfaces**:

```
auto eth0
iface eth0 inet dhcp
```

After a restart, there was still no network connection. I then opened **System > Preferences > Startup Applications** and unchecked **Network Manager**. After yet another restart, I had a full network connection. This persisted even after a third restart.

It's pretty clear from numerous similar threads in these forums that there are some serious problems with Network Manager. I hope these notes will help future sufferers.

JGB

---

### Post by Barriehie on 2010-01-30
Good!  Nothing worse than a linux box with no network, although I can recall the days of 300 baud modem too..... :)

Barrie

---

### Post by pillu on 2010-01-31
This didn't work for me either. Also stupidly I changed my dhclient.conf several times without taking backups and now my internet is badly broken. Can someone post me the contents of their dhclient.conf file with the intact rfc3442 reference in the request line?

---

### Post by jgb2185 on 2010-01-31
Pillu, the file you asked for is attached to this post. Note you will need to change its name to the original.

I believe that if you were to boot from the Ubuntu live CD, you would find a copy of the original file in the **/etc/dhcp3** directory.

JGB

---

### Post by lisati on 2010-01-31
Here's a couple of thoughts based on the minimal research I've done to help shed light on a possible solution.
1. The contents of /etc/network/interfaces **can** depend on the machine.
On my laptop (9.04 Desktop 32-bit), eth0 is not listed but can be managed by NM, but on my main desktop (9.04 server, 64 bit) has an entry, and NM doesn't seem to want to manage it.
2. Running "ifup" on my machines generates an error if the interface is already up, related to the connection already being up. (Yes, I know this isn't quite the same as what's being discussed.) I'm mildly curious to see if running something like the following would do anything useful (e.g. reset the interface or produce a different error message that provides additional informarion that might be helpful):
```
sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by pillu on 2010-02-01
Running ifup on eth0 gives the same error. It gets stuck when trying DHCP requests to the router.
@jgb thanks for the file. I forgot about the live CD :)...

---

