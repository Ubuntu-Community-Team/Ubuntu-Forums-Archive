---
title: "Wireless Issues"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by EastZephyr on 2010-02-17
Hi, 

I'm new to Linux in general and just dual booted Ubuntu 9.10 onto my Dell Inspiron 1501.  After a successful install, I attempted to connect to Purdue University's wireless network (PAL2.0) using the wireless connections GUI and the settings described by the Purdue Linux Users group.  There was an unprotected network in the area so I tried to access that and was again unsuccessful.  Tonight I tried connecting to my home router and as thwarted for a third time.  It is of note that I can access all three networks from Windows with no problems.  

After some looking around I attempted to connect via the command line: 

```

ifconfig wlan0
wlan0              Link encap: Ethernet   HWaddr 00:1c:26:26:d3:31
                         BROADCAST MULTICAST    MTU: 1500   Metric: 1
                         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                         collisions:0 txqueuelen:1000
                         RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)

sudo ifconfig wlan0 down
[sudo] password for (user):
sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

```

This isn't the entirety of what i attempted but its as far as I could get (ie i spent several hours searching different forums and couldn't find a solution).  

Anyone have any ideas? 

-Bryant

---

### Post by chicoharv on 2010-02-17
Can you connect ethernet (hard wired) with ubuntu? If you can, download all new packages first, then download the driver for your wireless card. Now try to use the wireless networks.also look on the forum under networks for specific packages to install for your wireless card.

---

