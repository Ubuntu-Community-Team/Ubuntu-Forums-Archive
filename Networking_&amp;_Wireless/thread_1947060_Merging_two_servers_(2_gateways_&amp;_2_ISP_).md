---
title: "Merging two servers (2 gateways &amp; 2 ISP )"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by Elmirix on 2012-03-26
Hello Guys, 

This is my first post here at ubuntuforums, I was wondering if i can get some help around here regarding a small project that i'm trying to work it out.

Currently at my place I have two ubuntu servers 10.04 and each box with independent ISP but they join the same LAN just different LAN IPs.


Server 1 192.168.5.1 <---gateway in LAN
Server 2 192.168.5.2 <---gateway in LAN

Both servers currently are doing routing and working with no problem and users get different gateways according to my DHCP setup... no problem.

Now, I'm trying to use only 1 server to do this job, so I'm running a test box with 3 NICs.

2 NICs for each ISP (eth0 & eth1) and 1 NIC to my LAN with virtual IPs 192.168.5.1 & 192.168.5.2 (eth2 and eth2:1)

I'm trying to setup that any user using gateway 192.168.5.1 (eth2) will use ISP1 and others using 192.168.5.2(eth2:1) will use ISP2.

I have being trying some other stuff but I'm really lost here; can i get some help here.

Thanks in advance I hope I'm clear enough

---

### Post by iiz on 2012-03-26
If you are up for some fun you can install vyatta it's a cisco like router software for linux. I have always wanted to try it, looked like a lot of fun, I just never had the time to sit down and mess with it.

Vyatta has loadbalancing, which means you can have 2,3,4 or however many gateways and it will evenly balance network load amongst them.

An easier option would be to install untangle, this will trash your server though since it requires a dedicated box. So if you were planning on running other services that's out of the question. Untangle charges money for the load balancer, but it's all GUI based. I have one deployed at my current office. I'm not wholly satisfied with it's performance since the web UI is a bit buggy, but other than that it's served me well.

Vyatta is completely free I believe.


If you don't want load balancing you could check out the advanced features of iptables, i think it might be able to direct traffic for you using the NAT functions, not sure though.

PS upon rereading your question i think i misinterpreted you at first. If i got it right, you had two servers, both with DHCP running on them, running on the same LAN at the same time? That would cause conflicts, nasty conflicts lol :) If my above answers aren't sufficient could you clarify your setup and what services are running on those two servers and also how exactly do you want those clients to access the Internet, through a gateway server or direct to your modem/router?

---

### Post by Elmirix on 2012-03-26
Currently both servers are running on the same LAN with different IP.

Each server holds an ISP and acts as a gateway in my network. Only one server controls DHCP and i have static configuration to clients on my LAN.

Im not looking in doing load balancer. Just with the new server keep both IPs on the LAN and who ever uses IP-GATEWAY-ONE will use ISP1 (192.168.5.1) and who ever uses IP-GATEWAY-TWO the server will choose ISP2 (192.168.5.2).

Currently there is no conflicts on the network. Im only downsizing 1 server to conserve energy.

I know with iptables there has to be a way to make this happen. But i cant find a solution yet for this. 

Ill read about Vyatta.

---

### Post by Elmirix on 2012-03-27
How can i move this thread to the networking section?

---

### Post by Iowan on 2012-03-27
> **Elmirix said:**
> How can i move this thread to the networking section?Use the "Report abuse" button, a moderator should be able to help.

Oh look, it's already done. ):P

---

### Post by Elmirix on 2012-03-30
I believe that this is not possible. tried different ways.

---

