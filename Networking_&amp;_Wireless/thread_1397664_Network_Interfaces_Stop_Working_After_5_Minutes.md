---
title: "Network Interfaces Stop Working After 5 Minutes"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by billmanhillman on 2010-02-03
Please help. My network interaces stop working after 5-10 minutes of operation.
I have 2 network cards, one static IP and the other dhcp. Sometimes I can ping my router, other times I can't.
 
[solved] see last entry.......

---

### Post by Iowan on 2010-02-03
What kind(s) of cards? I've seen similar threads, but don't immediately remember cause/cure (I'll look for them).

---

### Post by cariboo on 2010-02-03
Moved to Networking & Wireless

---

### Post by billmanhillman on 2010-02-03
They are dual NVIDIA nForce 570 SLI MCP integrated controllers. And they just started acting like this.

---

### Post by billmanhillman on 2010-02-04
This is without a doubt, an issue with Ubuntu. Running on windows doesn't have this issue. The gateway is fine. 
 
nslookup works
I can ping the gateway
I cannot ping 4.2.2.2
Firefox doesn't work
Chromium doesn't work
I'm using Ubuntu 9.10 (for about 3 months now)
I just started having this problem a couple weeks ago
I noticed another user was having the same issue a week ago, but nobody could help in his/her thread.
 
My network interfaces show: (looks strange to me)
 
_____________________________________
 
Wired Networks (nVidia MCP55 Ethernet)
Static Card
Disconnect
------------------Available---------------
ifupdown (eth0)
Wired Networks (nVidia MCP55 Ethernet)
DHCP Card
Disconnect
-----------------Available---------------- 
ifupdown (eth1) 
_________________________________ 
VPN Connection 
_____________________________________
 
](*,)

---

### Post by billmanhillman on 2010-02-04
Here is a screenshot of the interfaces

---

### Post by Iowan on 2010-02-04
Do both interfaces show an IP address (**ifconfig -a**)?

---

### Post by billmanhillman on 2010-02-05
Yes, both interfaces show an ip address.

---

### Post by billmanhillman on 2010-02-07
Bump

---

### Post by billmanhillman on 2010-02-09
Bump!

---

### Post by Iowan on 2010-02-09
The interfaces retain their IP Addresses even after they stop working? Does **route -n** show any changes between working and non-working?

---

### Post by billmanhillman on 2010-03-01
Yes, they keep the ip address but they don't work. As a matter of fact, I just rebooted and disabled my dhcp card. The only card I have that is active is the static IP card. With that said, it stopped working after 2 minutes. I disconnected and reconnected the static card from the menu bar. After that, I get the same static IP. However, I cannot ping the gateway.
 
If I type "route" it suddenly finds the gateway. (I can ping it). I still can't get out to the internet. However, I can ping 4.2.2.2. So it seems to be a dns issue.
 
What gives?

---

### Post by billmanhillman on 2010-03-02
Solved.
 
You should not define interfaces in /etc/network/interfaces if you're using the network manager applet. you should remove all the interfaces except the ones with "lo" in them. It's either one or the other, but not both.

---

### Post by Iowan on 2010-03-02
Well, it's kinda sad that things have de-volved, but good to know. Thanks for confirming what I've read elsewhere...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

