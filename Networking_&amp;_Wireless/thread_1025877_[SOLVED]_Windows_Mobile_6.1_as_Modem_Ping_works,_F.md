---
title: "[SOLVED] Windows Mobile 6.1 as Modem: Ping works, Firefox not"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by kaefert66014235 on 2008-12-30
Hi there! I'm trying to use my Windows Mobile 6.1 device (HTC Touch HD) as modem for my Ubuntu 8.10 laptop. It seems to work quite nice with the modem mode of Windows Mobile 6.1

Ubuntu detects a new network card eth1 and I get a nice adress assigned by dhcp (device seems to function as dhcp server) when attaching the device:
```
kaefert@Mobulux:~$ ifconfig eth1
eth1      Link encap:Ethernet  Hardware Adresse 80:00:60:0f:e8:00  
          inet Adresse:192.168.0.102  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::8200:60ff:fe0f:e800/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1478  Metrik:1
          RX packets:27 errors:18 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:2418 (2.4 KB)  TX bytes:5283 (5.2 KB)
```

Also the routes look correct to me:
```
kaefert@Mobulux:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

I can ping 192.168.0.1 and [www.google.at:](www.google.at:)
```
kaefert@Mobulux:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=3.07 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=1.57 ms
^C
--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1005ms
rtt min/avg/max/mdev = 1.574/2.325/3.077/0.753 ms
kaefert@Mobulux:~$ ping www.google.at
PING www.l.google.com (74.125.39.147) 56(84) bytes of data.
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=1 ttl=235 time=118 ms
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=2 ttl=235 time=75.3 ms
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=3 ttl=235 time=98.2 ms
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=4 ttl=235 time=103 ms
^C
--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3015ms
rtt min/avg/max/mdev = 75.372/98.870/118.617/15.503 ms
kaefert@Mobulux:~$ 
```

So this means google is reachable and the dns-name gets resolved. Lets open Firefox and browse [http://www.google.at/](http://www.google.at/) -->
no google, no error-page --> only endless loading --> the tab header writes: "Loading..." and the status bar writes: "waiting for www.google.at"

What could be the reason for this? the goal seems so near..

EDIT: I found out that both ssh & vncviewer to a host on the internet are working. Also working are Skype and the Gmail Notifier.

---

### Post by Rohan Kapoor on 2008-12-30
> **kaefert66014235 said:**
> Hi there! I'm trying to use my Windows Mobile 6.1 device (HTC Touch HD) as modem for my Ubuntu 8.10 laptop. It seems to work quite nice with the modem mode of Windows Mobile 6.1

Ubuntu detects a new network card eth1 and I get a nice adress assigned by dhcp (device seems to function as dhcp server) when attaching the device:
```
kaefert@Mobulux:~$ ifconfig eth1
eth1      Link encap:Ethernet  Hardware Adresse 80:00:60:0f:e8:00  
          inet Adresse:192.168.0.102  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::8200:60ff:fe0f:e800/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1478  Metrik:1
          RX packets:27 errors:18 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:2418 (2.4 KB)  TX bytes:5283 (5.2 KB)
```

Also the routes look correct to me:
```
kaefert@Mobulux:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```

I can ping 192.168.0.1 and [www.google.at:](www.google.at:)
```
kaefert@Mobulux:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=3.07 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=1.57 ms
^C
--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1005ms
rtt min/avg/max/mdev = 1.574/2.325/3.077/0.753 ms
kaefert@Mobulux:~$ ping www.google.at
PING www.l.google.com (74.125.39.147) 56(84) bytes of data.
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=1 ttl=235 time=118 ms
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=2 ttl=235 time=75.3 ms
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=3 ttl=235 time=98.2 ms
64 bytes from fx-in-f147.google.com (74.125.39.147): icmp_seq=4 ttl=235 time=103 ms
^C
--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3015ms
rtt min/avg/max/mdev = 75.372/98.870/118.617/15.503 ms
kaefert@Mobulux:~$ 
```

So this means google is reachable and the dns-name gets resolved. Lets open Firefox and browse [www.google.at](www.google.at) -->
no google, no error-page --> only endless loading --> the tab header writes: "Loading..." and the status bar writes: "wait for www.google.at"

What could be the reason for this? the goal seemed so near..
The speed on these devices is sometimes very slow. It will take time for a webpage to load on a cellular connection!

---

### Post by kaefert66014235 on 2008-12-30
> **darth-vader said:**
> The speed on these devices is sometimes very slow. It will take time for a webpage to load on a cellular connection!

Thanks for your answer, but that can't be the only reason. Web browsing is not slow, absolutly NO answer from webservers arrive at my browser.

This is what wget writes me when i tell it to browse google:
```
kaefert@Mobulux:~$ wget http://www.google.at
--2008-12-30 22:08:12--  http://www.google.at/
Auflösen des Hostnamen »www.google.at«.... 74.125.39.99, 74.125.39.103, 74.125.39.104, ...
Verbindungsaufbau zu www.google.at|74.125.39.99|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... ^C
```

And I tried this a few times and always waited for at least 5 minutes each time. and no connection will take more than 5 minutes for transmitting a header.

EDIT: btw, the phone tells me the connection works on HSPA right now, which shouldn't be that slow

---

### Post by Rohan Kapoor on 2008-12-30
Allright, that could mean that Ubuntu isn't connecting to your network properly. Have you tried seetings for dial up in the network manager?

Edit: 5 minutes is way too long!

---

### Post by kaefert66014235 on 2008-12-30
> **darth-vader said:**
> Allright, that could mean that Ubuntu isn't connecting to your network properly. Have you tried seetings for dial up in the network manager?

Edit: 5 minutes is way too long!


It seems to me, as if using these windows mobile 6.1 devices as modems doesn't work like using normal modems. When you connect the device while it is configured to act like a modem to a PC, the PC will detect it as a LAN-Card (Network-Manager calls it "High Tech Computer Generic RNDIS") which is connected to a Network. The WM6.1 device then seems to act as a dhcp server and gateway giving me the adress 192.168.0.102 and itself the adress 192.168.0.1;
This works quite well (see posts above) except for browsing.

I don't see what I could do to truly use the device as a modem, like conventional modems from huawei and the like.

---

### Post by Rohan Kapoor on 2008-12-30
How is this device connecting to your computer, over a cable or bluetooth?

---

### Post by kaefert66014235 on 2008-12-30
> **darth-vader said:**
> How is this device connecting to your computer, over a cable or bluetooth?

an USB-Cable

EDIT: I think I may have found something: on that page (German) [http://forum.ubuntuusers.de/topic/internetfreigabe-eines-windows-mobile-geraets](http://forum.ubuntuusers.de/topic/internetfreigabe-eines-windows-mobile-geraets)
a guy states, that changing the MTU to 1394 made the trick.
I tried to change it with the Network-Manager, however, if I call "ifconfig eth1" I still see an MTU of 1478. I will go and search now how to change that MTU value with command line tools. I will update you if I have news.

EDIT2: HAHA! THATS IT! I just had to call "sudo ifconfig eth1 mtu 1394" after connecting and it WORKS! im writing this over that connection already! :)

---

### Post by Rohan Kapoor on 2008-12-30
Great for you, sorry I wasn't too much help!

---

### Post by kaefert66014235 on 2008-12-30
> **darth-vader said:**
> Great for you, sorry I wasn't too much help!

You know the TV-series Dr. House?
Where he always needs his team to talk to him so that he gets the good ideas?
You've been my team on this one ;)

thanks for talking to me! :D

---

### Post by Rohan Kapoor on 2008-12-30
> **kaefert66014235 said:**
> You know the TV-series Dr. House?
Where he always needs his team to talk to him so that he gets the good ideas?
You've been my team on this one ;)

thanks for talking to me! :D
Yeah I know the series but not very well.

Glad to be of assistance.

Your Welcome!!!

---

### Post by Manthis on 2009-07-03
Hi guys,

I'm presently trying to connect to the Net with my HTC Touch HD.
Like you kaefert, I get an eth1 interface and then using dhclient I get the IP: 192.168.0.102 for this interface.

However, I can't ping anything else than 192.168.0.1 or browse the Web through firefox, etc, etc...

There might be a difference with you, because I use wicd instead of NetworkManager and I'm under kubuntu 9.04 jaunty.

Is anyone able to give me a hand?

---

### Post by kaefert66014235 on 2009-07-08
> **Manthis said:**
> Hi guys,

I'm presently trying to connect to the Net with my HTC Touch HD.
Like you kaefert, I get an eth1 interface and then using dhclient I get the IP: 192.168.0.102 for this interface.

However, I can't ping anything else than 192.168.0.1 or browse the Web through firefox, etc, etc...

There might be a difference with you, because I use wicd instead of NetworkManager and I'm under kubuntu 9.04 jaunty.

Is anyone able to give me a hand?

I don't use networkmanager for eth1, it doesn't work well if I do.

Did you try to set the MTU value for the networkadapter that leads to your windows mobile 2006 device?

---

### Post by Rohan Kapoor on 2009-09-02
> **Manthis said:**
> Hi guys,

I'm presently trying to connect to the Net with my HTC Touch HD.
Like you kaefert, I get an eth1 interface and then using dhclient I get the IP: 192.168.0.102 for this interface.

However, I can't ping anything else than 192.168.0.1 or browse the Web through firefox, etc, etc...

There might be a difference with you, because I use wicd instead of NetworkManager and I'm under kubuntu 9.04 jaunty.

Is anyone able to give me a hand?
Change the mtu and you should be fine. Recently I got a windows mobile 6.1 device (Sony Ericsson XPERIA X1) and it needs the same.

---

