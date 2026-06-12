---
title: "Cannot Connect to NanoStation2 LAN"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by hansteam on 2010-11-24
Hey folks.

I've been digging around the forum for a couple hours, and I'm afraid I've run out of ideas for connecting to the internet via my new NanoSystem2.

When I boot the system it displays "wireless networks available," but I'm trying to access my wired network. I found posts instructing me to disable ipv6 (which I've done), edit /etc/network/interfaces (which I've done), and run the dhclient utility (which I've done). I am able to connect to NanoSystem2 with no problems from my Windows 7 partition. I launched the command prompt and got the ipconfig information to use in the manual entry for ipv4. Still, I could not connect via LAN. I'm sure I'm missing something simple and silly, but I've been working on this for a couple hours and still have had no luck.

By the way, if it's helpful:

```
lspci | grep Eth
```

Gives me:

```
Ethernet: Atheros Communication inc. AR8152 v1.1 Fast Ethernet rev(c1)
```

I'm running Ubuntu 10.04 on a Toshiba Satellite.

Any help would be greatly appreciated!

---

### Post by hansteam on 2010-11-24
I found [this post]("http://ubuntuforums.org/showthread.php?t=86389&highlight=troubleshooting") and tried some of the tests that it recommended. I couldn't run ethtool because it was not installed. I just downloaded the source for the tool and I'll see if I can download it next time I launch my Ubuntu partition. Anyway, here are the tests I ran and their results:

```
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:18:29:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ethtool is not installed

~$ mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found

$ ping 192.168.1.100
connect: Network is unreachable

$ ping 192.168.30.1
connect: Network is unreachable

$ ping 192.168.1.20
connect: Network is unreachable

$ dmesg | grep lan
[   17.210136] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

Any help would be greatly appreciated. I'm forced to run Windows 7 for internet access right now, and it's terrible. It seems to have a stutter, and it's already done one auto shutdown after I thought I rejected it :(

---

### Post by hansteam on 2010-11-24
I just tried calling the ISP's technical support. The representative had never heard of Ubuntu and was "unfamiliar" with linux.

---

### Post by hansteam on 2010-11-29
I wound up purchasing a wireless router that is now sitting between my computer and the NanoStation. I wanted it anyway so I can get wireless access, but it seems strange that I'm unable to connect directly.

---

