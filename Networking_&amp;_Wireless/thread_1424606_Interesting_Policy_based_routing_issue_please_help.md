---
title: "Interesting Policy based routing issue please help"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by test006 on 2010-03-08
Hi,
I have two ADSL connections to the internet with following setup (in my case policy based routing is not quite straight forward):

---A1---\ 
      |Ethernet switch|-------Linux Proxy Server 
---A2---/   PC1  PC2
            
PC1, PC2, A1, A2 and Linux Proxy all connect via a single Ethernet switch. I have also attached a jpg image see attachment.
On linux I run it as proxy server using SSH forwarding. 
Linux server has only one network port i.e. eth0 only.
Using PC1 i establish SSH connection using putty which is configured to do ssh forwarding under the tunnel configuration in putty.
PC1 firefox web browser is configured to use SSH tunnel as its SOCKS proxy. 
This configuration works fine when i have one ADSL connection i.e. A1 only. A1 and A2 are ADSL modems.
By default linux server is configured with a default route to A1's IP address which is 192.168.1.254 and it has IP address of 192.168.1.1/24 on its eth0 intf.
Now i want my traffic from PC1 to go via A2 connection using policy based routing. PC2 would go via A1 using the default route on the linux server i.e. 192.168.1.254.
So on the linux server i have added another IP address of 172.168.1.1/24 on the eth0 intf. A2's LAN interface IP address is 172.168.1.254/24
I have created a routing table in /etc/iproute/rt_tables:
> 2 test
I have added a default route in the test routing table:
> ip route add default via 172.168.1.254 tab test
I have added a IP rule to forward all the traffic from source IP address of 172.168.1.200 (PC1) to go via tab test:
> ip rule add from 172.168.1.200/32 tab test
From PC1 i have establish a ssh session using putty and try to browse and my traffic still goes via A1 connection and there is no traffic on A2 link. Please note on PC1 i now have only configured 172.168.1.200 IP address so this makes sure that my source of traffic is 172.168.1.200. The only thing is that i am using is the SSH session as a SOCKS 5 proxy. Can anyone tell me what am i doing wrong?
PC1 and Linux server:
    
Firefox using foxyproxy PC1<==>SSH tunnel SOCKS <==>Linux Proxy Server
 
Firefox on PC1 sends traffic to localhost which is than forwarded via the SSH tunnel to the Linux Proxy server.
After the traffic reaches Linux Proxy server i would imagine it would than send the traffic via A2 since my source is 172.168.1.200, i.e. it would do a look in test table and the nexthop would be A2 router. This is not whats happening it uses 192.168.1.1 address to send the traffic to A1 router.
Can some help and tell what i am doing wrong.
Thanks
If you need more clarification please let me know...

---

