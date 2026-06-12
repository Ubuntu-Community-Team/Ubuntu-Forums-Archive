---
title: "weird connectivity issues"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by oliox on 2013-08-31
Lately i've been having weird issues connecting to the internet.
Most of the time everything works ok but there seem to be some sites I can't access.
Specifically I can't access ffmpeg.org I've tried different browsers, tried using ping too, but noting worked.
I know it's not a problem with my home connection because i can connect to the site using other computers just fine.
Usually i can figure out these kinds of issues but I'm totally lost on this one.
Does anyone can shed some light on this issue?
Thanks for reading

---

### Post by steeldriver on 2013-08-31
Hello and welcome to the forum

Sometimes "weird connectivity issues" like this (in particular , specific domains being unreachable) are the result of path MTU discovery (PMTUD) issues - you can do a ping test to establish your max unfragmented MTU or just play with reducing your MTU in steps just to see if it helps - if you're using the standard desktop / network-manager applet there's an MTU box in the main connection editor tab that's set to 'automatic' by default, but you can enter a number there. If you want to try the ping test post back and I will try to dig out the exact command line.

---

### Post by oliox on 2013-08-31
Yes I would like to try the ping test.
I tried messing around the mtu but didn't archive anything.

---

### Post by houstonbofh on 2013-08-31
Step one is figuring out what is breaking.  If you ping it, does the IP resolve?  If you use wget does it get a file?

---

### Post by oliox on 2013-08-31
The ip gets resolved but i get no responses. I can't download using wget either

---

### Post by steeldriver on 2013-08-31
Well if you've already adjusted the MTU with no luck I'm not sure this will help but the ping probe is something like

```
ping -c1 -M do -s $((1500-28)) ffmpeg.org
```

where 1500 is your trial MTU - if the value is too large you will get a response like

```

$ ping -c1 -M do -s $((**1508**-28)) ffmpeg.org
PING ffmpeg.org (192.190.173.45) 1480(1508) bytes of data.
From lap-t61p.local (192.168.1.16) icmp_seq=1 **Frag needed and DF set** (mtu = 1500)

--- ffmpeg.org ping statistics ---
0 packets transmitted, 0 received, **+1 errors**

```

---

### Post by oliox on 2013-08-31
response I get 

```

ping -c1 -M do -s $((1500-28)) ffmpeg.org
PING ffmpeg.org (192.190.173.45) 1472(1500) bytes of data.
From jpcnix.local (192.168.1.67) icmp_seq=1 Destination Host Unreachable

--- ffmpeg.org ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

 
```

---

### Post by steeldriver on 2013-08-31
Oops sorry I think I misread your original post - if you can't get a ping response at all (i.e. host unreachable) then that would indicate a lower level routing problem, I think

I don't really know what to suggest - perhaps looking at ifconfig and route -n?

```
ifconfig
```

```
/sbin/route -n
```

---

### Post by oliox on 2013-08-31
ifconfig looks normal 

route -n is 
 ```

$ /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.0.0.0       0.0.0.0         255.0.0.0       U     9      0        0 wlan0


```

---

### Post by steeldriver on 2013-08-31
Can we at least see the "Mask: " value from your ifconfig?

---

### Post by oliox on 2013-08-31
mask is 255.0.0.0

edit: changed mask to 255.255.255.0 and it worked. Gah! what a dumb mistake! 
thanks for the tip and for your time :)

---

### Post by steeldriver on 2013-08-31
You're welcome :d

---

