---
title: "Wifi seems to work but no internet (u12.04)"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by marketwizard on 2012-08-28
Hello,

I'm new to this forum and quite new to Linux as well. I've been looking in various forums to find a solution to my problem but wasn't successful.

My Problem:
The internet is not working.

I installed Ubuntu 12.04 on a Acer PRO73Vm. The wireless network seems to be connected but when I try to open firefox the internet doesn't work.

It would be great if you could give me some guidance on what I could try to solve the problem.

Thank you for reading and I hope somebody can help!

---

### Post by sam1948 on 2012-08-28
Hi,

- does the internet work with other devices or with other OSs on that same computer?

- open a terminal, run the following and post the output

```
ifconfig
```

```
route
```

---

### Post by marketwizard on 2012-08-28
Thank you for your quick help!

The internet works with other devices including mac, win xp, win 7
Before I installed Ubuntu 12.04 the laptop ran on windows vista and the internet worked.

```
eth0      Link encap:Ethernet  HWaddr 00:22:15:ee:5c:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89217 (89.2 KB)  TX bytes:89217 (89.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:8a:64:6e  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fe8a:646e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:235959 (235.9 KB)  TX bytes:167861 (167.8 KB)
```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
```

---

### Post by miegiel on 2012-08-28
Can you ping 192.168.2.1 ?
```
ping 192.168.2.1
```
And does the gateway (the machine with 192.168.2.1) need to be configured to forward your machine to the internet?

---

### Post by sam1948 on 2012-08-28
i would check the connectivity with another device which u count-on.
in addition **restart the router is not a bad idea**.
(restart not reset, you don't want to configure it all again)

---

### Post by marketwizard on 2012-08-28
I forgot to mention that I have another laptop that runs ubuntu (11.04) and it can access the internet. 

@miegiel

Thank you for your help!

The ping output was:

```

PING 192.2.1 (192.168.2.1) 56(84) BYTES OF DATA.
From 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.102 icmp_seq=67 Destination Host Unreachable
From 192.168.2.102 icmp_seq=68 Destination Host Unreachable
From 192.168.2.102 icmp_seq=69 Destination Host Unreachable
From 192.168.2.102 icmp_seq=70 Destination Host Unreachable
From 192.168.2.102 icmp_seq=71 Destination Host Unreachable
From 192.168.2.102 icmp_seq=72 Destination Host Unreachable

```

I don't think the gateway needs to be configured to forward the machine. (mot sure if I understand you correctly). Every machine can access the internet independently.

---

### Post by miegiel on 2012-08-28
> **marketwizard said:**
> ...The ping output was:

```

**PING [COLOR="Red"]192.2.1[/COLOR] (192.168.2.1) 56(84) BYTES OF DATA.**
From 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.102 icmp_seq=67 Destination Host Unreachable
From 192.168.2.102 icmp_seq=68 Destination Host Unreachable
From 192.168.2.102 icmp_seq=69 Destination Host Unreachable
From 192.168.2.102 icmp_seq=70 Destination Host Unreachable
From 192.168.2.102 icmp_seq=71 Destination Host Unreachable
From 192.168.2.102 icmp_seq=72 Destination Host Unreachable

```

...
That's weird!? Did you make a typo?

Also: Could you elaborate a bit on you home network and internet connection setup? Do you only have one of those modem+router+firewall+switch+access-point boxes that connect everything together and to the internet, or is there more hardware involved?

---

### Post by marketwizard on 2012-08-28
@sam1948

I tried to restart the router but that didn't help. Other machines like the MacBookAir I'm writing this from are working fine.

@miegiel
You're right. It's a typo. I was typing it from the screen of the ubuntu machine.. May I ask what the ping output tells you?

There is a single device which is connected to the telephone line that is responsible for the network.
I hope that information is helpful.

---

### Post by nativehound on 2012-08-28
open firefox and type

[http://74.125.224.72/]("http://74.125.224.72/")
 
if google loads it's a dns issue.

---

### Post by marketwizard on 2012-08-28
@nativehound:

Unfortunately, google doesn't load.

---

### Post by marketwizard on 2012-08-29
The fact that there is a connection to the router but the internet is not working is strange. I don't know what the reason for this could be..

---

### Post by marketwizard on 2012-08-29
I tried to use the laptop with an ethernet cable and it worked.

---

### Post by nativehound on 2012-08-29
You could check rfkill to see if blocking is on

```
rfkill list
```

Most likley rfkill blocking is on.

To change 

```
sudo rfkill unblock wifi; sudo rfkill unblock all
```

recheck rfkill list

is should read no to both.

```
sudo /etc/init.d/network-manager restart
```


gl

---

### Post by sam1948 on 2012-08-31
can you ping to your router?

it's a strange one.

please run these and post:
```
traceroute google.com
```
```
traceroute 173.194.41.165
```
```
traceroute 192.168.2.1
```

---

