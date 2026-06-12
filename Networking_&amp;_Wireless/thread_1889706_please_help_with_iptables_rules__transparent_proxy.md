---
title: "please help with iptables rules / transparent proxy"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by robgr85 on 2011-12-01
Hi!

I have small server working 24/7 in my network (hosting my blog page, monitoring box, getting mail and serving squid proxy), but it is not the problem. There are several computers at my network, and I've decided to let them use my proxy from atom server. 

The squid server is in the same subnet as other PC-s, Laptops, and router with ADSL modem connected to the internet. Lets assume that my router ip is 192.168.1.1, my other network computers use 192.168.1.2-50, my atom server IP is 192.168.1.254.

I use DLink DSL-G604T router (its a gateway), which has linux on board, and I can configure its iptables as I like them to be.

I would like to set them, so the http traffic from network computers (IP:192.168.1.2 - 192.168.1.50) would be redirected to my proxy server (IP:192.168.1.254:3128), which uses router (IP: 192.168.1.1) as internet gateway.

I've googled some iptables rules for similar situations with squid used as transparent proxy, but none of them works. Help me please, the fight with iptables made me really tired.

---

### Post by Doug S on 2011-12-02
It isn't clear to me exactly what you are trying to do, but I wonder if this thread might help: [http://ubuntuforums.org/showthread.php?t=1855192](http://ubuntuforums.org/showthread.php?t=1855192)

---

### Post by robgr85 on 2011-12-02
> **Doug S said:**
> It isn't clear to me exactly what you are trying to do[/URL]

Sorry for my bad english. I will try to explain it one more time, if it is still unclear I will make an illustration and post it here. 

I want to set iptables on my router (which is ADSL gateway for all computers from network), so that web traffic from local LAN machines with IP range 192.168.1.2-192.168.1.50 would be redirected by the router to my transparent proxy server which is running on 192.168.1.254:3128. The proxy machine is using the same router as internet gateway. 

I don't want to configure proxy settings on every PC for every browser etc, that is why I thought that it would be nice to redirect LAN machines web traffic to squid using iptables at my router.

---

### Post by Doug S on 2011-12-03
I understand and also now understand the challlenges for creating the iptables rules. I probably found the same references as you on internet. Mostly they give the same solutions for iptables rules and mostly I do not understand how they can work. In my opinion several references confuse the distinction between the squid server and the router/firewall being the same machine or two seperate machines. However this reference seems very clear on the differences between the two: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Making_Your_Squid_Server_Transparent_To_Users](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid#Making_Your_Squid_Server_Transparent_To_Users) 
see section 9.1 and this sub-section "Squid Server and Firewall – Different Servers"
 
I hope this helps, and if not I can try to test some iptables rules ideas here.

---

### Post by robgr85 on 2011-12-04
> **Doug S said:**
> 
see section 9.1 and this sub-section "Squid Server and Firewall &#8211; Different Servers"
 
I hope this helps, and if not I can try to test some iptables rules ideas here.

Thanks much!! It finally works :) 

Just wonder, if saving settings on my router web interface will do the job with iptables changed from telnet connection. My router has iptables v1.2.6a
and there is no iptables-save utility.

I thought, that it would be good idea to learn more about iptables, could You recommend some good tutorials/courses about it?

---

### Post by Doug S on 2011-12-05
> I thought, that it would be good idea to learn more about iptables, could You recommend some good tutorials/courses about it?
Better understanding of iptables also requires good understand of TCPIP and good understanding of the connection tracking table (conntrack), in my opinion. Myself, I have struggled with this stuff, and find it to be a continuing saga. Anyway, my references list: (In no particular order. Many of the references contain links to other references. I deleted a few, and perhaps should have deleted more):
 
[default value of nf_conntrack_tcp_timeout_close_wait discussion]("http://www.gossamer-threads.com/lists/iptables/devel/65910")
[The Linux Documentation Project - Linux IP Masquerade HOWTO]("http://tldp.org/HOWTO/IP-Masquerade-HOWTO/stronger-firewall-examples.html")
[URL="http://tldp.org/HOWTO/IP-Masquerade-HOWTO/stronger-firewall-examples.html"]The Linux Documentation Project - stronger firewall example.
[/URL][CLOSE_WAIT description]("http://www.frozentux.net/ipsysctl-tutorial/chunkyhtml/netfilterreference.html#AEN690")
[URL="http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html"]Iptables Tutorial 1.2.2
[/URL][Linuxtopia Firewall Iptables]("http://www.linuxtopia.org/Linux_Firewall_iptables/")
[netfilter.org NAT-HOWTO]("http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO.html#toc9")
[Packet Filtering Notes - Prabhaker Mateti]("http://www.cs.wright.edu/~pmateti/InternetSecurity/Lectures/PacketFilter/index.html#An Example Firewall Setup")
[Ubuntu forums - an example ruleset.]("http://ubuntuforums.org/"http://ubuntuforums.org/archive/index.php/t-856798.html")
[wikipedia TCP]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol")
[tcp_fin_timeout description]("http://www.frozentux.net/ipsysctl-tutorial/chunkyhtml/tcpvariables.html#AEN370")
[tcp_close_wait_interval description]("http://www.sean.de/Solaris/soltune.html#tcp_close_wait_interval")
[FIN_WAIT_2 description]("http://httpd.apache.org/docs/1.3/misc/fin_wait_2.html")
[Easy Firewall Generator]("http://easyfwgen.morizot.net/gen/")
[Bodhi Zazen's (Ubuntu Guru) IPTables Primer]("http://bodhizazen.net/Tutorials/iptables/")

---

