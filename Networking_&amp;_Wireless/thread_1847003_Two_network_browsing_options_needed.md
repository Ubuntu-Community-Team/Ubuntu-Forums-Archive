---
title: "Two network browsing options needed"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by yndesai on 2011-09-20
I am working in the intranet where the internet access is restricted. But i am allowed to use my own broad band CDMA/3G over usb for browsing.

Now what is happening that is when i connect both the network connection i cannot browse internet site i have to disconnect LAN on eth0. 

Is there a way I can browse with both connections on. 

I tried doing so by installing two different browsers firefox and chrome using them with two different settings.

---

### Post by lmarmisa on 2011-09-20
I believe that your problem is related to the metrics of your two default routes (intranet gateway and 3G).

Please, when you are connected to both networks, open a terminal, type this command and post the result:

```

route -n

```

---

### Post by yndesai on 2011-09-20
Thanks for the prompt reply following is the output 

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.6.6.6        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.7.147.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.7.147.1      0.0.0.0         UG    0      0        0 eth0
```

---

### Post by ipadm on 2011-09-20
I have the same problem but additional problem is a proxy on wlan0:

```
Destination Gateway Genmask Flags Metric Ref Use Iface
77.109.0.225    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.123.0   0.0.0.0         255.255.255.128 U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.123.1   0.0.0.0         UG    0      0        0 wlan0
```Can it be fixed?

---

### Post by yndesai on 2011-09-20
I also have proxy on WLAN but I do not
use it since my intranet sites are available
even without proxy.

---

### Post by ipadm on 2011-09-20
> **yndesai said:**
> I also have proxy on WLAN but I do not
use it since my intranet sites are available
even without proxy.

Lucky you! My proxy is on the Novel Gateway and it is really stupid! But anyway with proxy or without it I can't connect through ppp0 when wlan0 is up.

---

### Post by yndesai on 2011-09-28
I have used the Graphical interface (default connection manager of ubuntu) to establish the connection over the CDMA/3G. 
 
Also I think that the CDMA/3G connection is having DHCP since there is no specified fixed IP address that is defined before connecting.
 
My LAN also supports DHCP.
 
Thanks
 
yndesai

---

### Post by ipadm on 2012-06-06
Why windows can easy handle it? Is it any few-steps solution for Ubuntu?

---

### Post by yndesai on 2012-07-19
> **ipadm said:**
> Why windows can easy handle it? Is it any few-steps solution for Ubuntu?

on windows also i need to disable proxy for wlan. And at times intranet pages are not seen.

---

