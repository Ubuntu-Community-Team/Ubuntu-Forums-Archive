---
title: "How can I tell WHICH connection Ubuntu is actually using? (wlan0, wlan1, eth0, etc.)"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2012-03-27
How can I tell WHICH connection Ubuntu is actually using? 

Googling, some suggest I use the **"route"** command (but I'm not sure what it's actually telling me about which connection (wlan0, wlan1, eth0, etc.) Ubuntu is actually using.
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
10.20.30.0      *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         10.20.30.40     0.0.0.0         UG    0      0        0 wlan0

```

Others say to use the **"arp"** command (again, I'm not sure what it's telling me).

```

$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.18             ether   00:14:d1:22:a3:93   C                     eth0
10.20.30.40              ether   00:16:b6:23:4f:96   C                     wlan0
192.168.0.54             ether   00:27:22:3e:ff:23   C                     eth0
192.168.0.20             ether   00:26:82:25:2a:16   C                     eth0

```

May I ask what command tells me, beforehand, which network interface Ubuntu will use?

---

### Post by jaybutts on 2012-03-27
you could for example in one shell get a ping going for google.com and then tcpdump -i eth0|grep google.com

and then see what you can pickup, basically use tcpdump if you don't want to use a graphical monitoring tool.

you can also just use netstat or something, for what reason and/or why are you looking for this?

---

### Post by rocksockdoc on 2012-03-27
> **jaybutts said:**
>  why are you looking for this?

Good question.

I have multiple ISP providers, all WISP (three to be exact) that I'm testing out performance of at the same time.

All of this is being done with temporary setups, e.g., this is outside pointing at one of them.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215029&stc=1&d=1332883368[/IMG]

In my comparisons, I have all three running at the same time because it's a royal pain to disconnect one set and then reconnect them up again. 

So, with all three 'available', I simply need to know which one is being used at any one moment for my test purposes.

---

### Post by rmil on 2012-03-27
By using ```
route -n
``` command you can always see through what IP number, internet goes. In your case it is wlan 10.20.30.40 you have flag UG.

You can always change that by giving another route to differnt ISP
deleting old route
```
route del default gw y.y.y.y wlan0
```
and adding new
```
route add default gw x.x.x.x eth0
```

I am using that I have 2 ISPs

---

### Post by rocksockdoc on 2012-03-28
> **rmil said:**
> By using "route -n", you can always see through what IP number, internet goes. In your case it is wlan 10.20.30.40 you have flag UG

How does this look for a plan to follow what you just said to do?
```
$ ifconfig
Reveals ... 
wlan0 ==> inet addr:10.20.30.159  Bcast:10.20.30.255  Mask:255.255.255.0
eth0 ==> inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
```Running the suggested command:
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.20.30.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         10.20.30.40     0.0.0.0         [COLOR=DarkRed]**UG **[/COLOR]   0      0        0 wlan0

```And, adding anything of value from the route command:
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
10.20.30.0      *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         10.20.30.40     0.0.0.0         **[COLOR=DarkRed]UG[/COLOR]**    0      0        0 wlan0

```Then, to change it, you suggest I go from:
```

$ sudo route del default gw 10.20.30.40 wlan0

```To what IP address?

Do I pick the IP address of the radio (which is currently set up as a bridge?)
```

$ sudo route add default gw**[COLOR=DarkRed] 192.168.0.100[/COLOR]** eth0

Unfortunately, this results in the error:
[COLOR=DarkRed]** SIOCADDRT: No such process**[/COLOR]


```

So, I think I'm close to being able to switch, at will, between eth0 and wlan0 (if it weren't for that error above).

Maybe I put the wrong IP address in the "route add" line?
How do I get that IP address to set to the default for eth0?
Is it the gateway IP address of the WISP radio which is connected to the laptop eth0 port? 
Or, do I use the gateway IP address as set up in that WISP radio?

---

