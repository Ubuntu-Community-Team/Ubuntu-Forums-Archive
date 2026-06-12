---
title: "Bridging to XP"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by IUNIXI on 2011-04-01
Hello all,

My laptop, which is my main machine, is running Ubuntu 10.10 I am bridging my wireless connection on my laptop to my Dell desktop; but I have somewhat of an issue. I was able to bridge the connection with ease, but the IP the XP machine has been assigned is not in my subnet. The issue is that I need to port forward to this machine, but my router doesn't recognise that the PC is on the network because it has a random IP.

I've tried assigning a static IP on the XP machine itself, but it doesn't change... Any help is appreciated, thank you!

---

### Post by patryk77 on 2011-04-01
A bit more information would be useful.

What is the IP address the XP box was assigned?

What steps did you use to bridge the connections?

The output of "ifconfig" on the Ubuntu box, at the very least...

Also, what do you mean by "it doesn't change" :confused:

It doesn't accept a static IP?

---

### Post by IUNIXI on 2011-04-01
> **patryk77 said:**
> A bit more information would be useful.

What is the IP address the XP box was assigned?

What steps did you use to bridge the connections?

The output of "ifconfig" on the Ubuntu box, at the very least...

Also, what do you mean by "it doesn't change" :confused:

It doesn't accept a static IP?

Sorry for the lack of information.

To bridge the connections, I just edited eth0 with Network Manager and changed it to "Shared". Rebooted, worked just fine.

The output of "ifconfig wlan0" on my Ubuntu machine:

```

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:26:5e:7c:37:b4  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe7c:37b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76864695 (76.8 MB)  TX bytes:3377141 (3.3 MB)

```The output of "ipconfig" on the XP machine:

```

IP Address. . . . . . . . . . . 10.42.43.83
Subnet Mask. . . . . . . . . . . 255.255.255.0
Default Gateway. . . . . . . . . . . 10.42.43.1

```When I tried assigning the static IP to the XP machine, after reboot, the IP was the same. Is there anything i can do on my Ubuntu machine to assign a different IP to the bridged connection?

---

