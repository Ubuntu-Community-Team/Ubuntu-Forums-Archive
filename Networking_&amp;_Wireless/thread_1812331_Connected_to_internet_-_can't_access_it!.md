---
title: "Connected to internet - can't access it!"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by d_btc on 2011-07-26
Okay, so I'm a total Ubuntu newbie - I had problems installing it on my blank hdd but eventually got it working.

Now I have encountered another issue - connecting to the net. I don't know if it's because the settings I'm putting in are wrong, I have no idea, and I have no idea where to start. I've tried ifconfig commands to find any helpful information and I just don't get it.

Basically, I'm running a wireless connection on my Vista laptop (that I'm speaking to you on now) which works fine.

My flatmate's wired connection to his PC works too.

Yet I copy over what seems to be the correct networking settings into Ubuntu, and it tells me "Wired connection 1 - connection established" yet it won't ping google.com or actually access the internet.

I tried calling my ISP and they don't offer ubuntu support, what a surprise -_-

What am I doing wrong?

---

### Post by ajgreeny on 2011-07-26
Can you show us the output of ```
ifconfig
``` and ```
cat /etc/network/interfaces
``` please.  It might help us figure out the problem.

Can you also check if pinging the router works.  The router IP should be under the router on a label, usually 192.168.x.y where x & y can vary but is often 0 and 1, or 1 and 1.

---

### Post by d_btc on 2011-07-26
on pinging the router, i get "network is unreachable" :s

here are the results of those bits of code.

```
  [FONT=&quot]gem@Gem-1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:55:0d:aa  
          inet6 addr: fe80::222:15ff:fe55:daa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:14648 (14.6 KB)
          Interrupt:41 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8784 (8.7 KB)  TX bytes:8784 (8.7 KB)
[/FONT]
  
```and

```
  [FONT=&quot]gem@Gem-1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
[/FONT]
  
```



oh, and its currently not saying its connected in ubuntu. but its still connected in vista.

---

### Post by Peter09 on 2011-07-26
disconnect your wired connection and then do the command and provide the output
 
```
nm-tool
```
 
also if you can connect via wireless and provide the output of the command
 
```
route
```

---

### Post by d_btc on 2011-07-26
```
  [FONT=&quot]NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:55:0D:AA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
[/FONT]
  
```

i can't connect via wireless, the pc doesn't have a wireless card - sorry!

---

### Post by Peter09 on 2011-07-26
Sorry - my mistake.
 
can you do these commands with your wired connection established.
 
```
nm-tool
```
and
```
route
```
 
and show us the output.

---

### Post by d_btc on 2011-07-26
Now I'm having the problem that it won't establish at all :S

nm-tool just results in the same info as when the cable isn't even plugged in.

route just comes up with

```
Kernel IP routing table
Destination           Gateway               Genmask         Flags Metric Ref         Use Iface
```


with nothing else.

---

