---
title: "Network manager says &quot;Wired network connection,&quot; but no internet"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by Monona on 2009-07-15
I've just starting running Ubuntu on my newly scavenged PC, but I'm unable to connect to the wired network.

When I plug in the ethernet cable, the network manager says "Requesting a network address from the wired network...", and then it tells me "Connection Established."  Then, when I try to load a page in Firefox or use apt-get to upgrade (i'm using Feisty 7.04, since i have an old install disk), I can't connect.

What can I check to see what the problem is?  I have a Broadcom BCM4401 ethernet interface.

I also have an extra network card I could try installing, but I'm worried that I won't be able to install the necessary drivers without a working network connection.

Thanks!

---

### Post by azr on 2009-07-15
Are you connecting the PC to a router? If so you may want to check that the router has successfully connected to internet. It could be that your computer is connected to the router, but the router not to the internet. Check that the appropriate lights are on, on your router. (In my case it would the the ADSL and PPP lights - but check the router manual for details of yours.)

---

### Post by prshah on 2009-07-15
> **Monona said:**
> 
What can I check to see what the problem is?

Most likely a DNS issue; can you open a terminal (Applications-Accessories-Terminal) and give the following commands and post back the output?```
sudo mii-tool eth0 # checks physical connection
ifconfig eth0 # shows network information
cat /etc/resolv.conf # shows DNS server information

```

---

### Post by Monona on 2009-07-16
@azr - Actually, the modem is hooked directly up to my computers, and appears to be connected to the internet, since all the lights are on, and it connects just fine with my laptop (which is how i'm posting this).

@prshah - I believe DNS is configured properly, but here are the outputs:

sudo mii-tool eth0 # checks physical connection
eth0: negotiated 100baseTx-FD, link ok

ifconfig eth0 # shows network information
eth0   Link encap:Ethernet  HWaddr 00:02:E3:35:3F:4E
       inet6 addr: fe80::202:e3ff:fe35:3f4e/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
       RX packets:13688 errors:1 dropped:1 overruns:0 frame:0
       TX packets:317 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:879108 (858.5 KiB)  TX bytes:31463 (30.7 KiB)
       Interrupt:17

cat /etc/resolv.conf # shows DNS server information
nameserver 208.67.222.222
nameserver 208.67.220.220

Now, what does that all mean then?  

Thanks!

---

### Post by Veloteuton63 on 2009-07-16
Similar problem here (I think). Except - my ethernet access worked before, from the same computer (this one) to the same router / modem (this one).
I'm currently using both (from another distro.).
So I'm fairly clueless here

---

### Post by Monona on 2009-07-17
Well, it was as simple as turning off the modem, turning it back on, plugging the ethernet cable into the desktop, and turning the desktop back on.

Don't I feel silly!

---

