---
title: "help debugging routing tables with netstat"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by nikhilbhardwaj on 2010-03-20
how do we know whats wrong with the routing table 
by seeing the output of netstat

```

You are troubleshooting a network problem and netstat -rn gives you
the following output. What is the problem and what command would
you use to fix it?
Destination      Gateway   Genmask         Flags MSS Window irtt Iface
128.138.202.0  0.0.0.0    255.255.255.0    U      40    0          0   eth0
127.0.0.0         0.0.0.0    255.0.0.0           U      40    0          0   lo

```this question is from chap 19, linux administration handbook
i've just read the chapter and cant seem to understand this

any clue guys??

---

### Post by Iowan on 2010-03-20
What do you see when you run it on your machine? Mine doesn't report "lo" information, has "0" for MSS, and has a line for the gateway. I don't have the linux administration handbook - what topics does chapter 19 cover (route, ping, MSS/MTU, etc., ...)?

---

### Post by nikhilbhardwaj on 2010-03-21
chapter 19 is network management and debugging
it includes
ping, traceroute, netstat, packet sniffers(tcpdump and ethreal)

```

$ netstat -rn
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
10.2.5.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
127.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 lo
0.0.0.0 192.168.1.254 0.0.0.0 UG 0 0 40 eth0

```

my guess was that the default gateway entry is missing??
how can we add it with route add??

---

