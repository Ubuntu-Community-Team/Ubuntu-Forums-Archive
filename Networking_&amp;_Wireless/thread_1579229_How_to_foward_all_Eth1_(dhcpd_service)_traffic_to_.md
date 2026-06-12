---
title: "How to foward all Eth1 (dhcpd service) traffic to Tun0 (openvpn)"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by torontobc on 2010-09-21
Hi Everyone,

In nutshell: 
I need to send all SIP/UDP traffic of eth1 (dhcpd server) to tun0 (openvpn tunnel) without sending the dhcpd requests to tun0.

OR

Just simply allow all the DHCPd clients of Server B to be able to ping Server A via the OpenVPN tunnel that exists.


In detail:
I have two servers:

Server A running Asterisk and OpenVPN Server.

Server B running DHCPd and has two NIC cards. Eth0 is the WAN to ISP. Eth1 is the NIC that feeds the Switch with DHCPd IPs to endpoint SIP phones.

Server A and Server B are miles and miles away from each and are connected to the internet either via Eth0 through their own ISPs.

OpenVPN on Server A is set to IP range 172.15.0.0/24 so Server A and B can ping each other in that range with 172.15.0.1 assigned to Server A.

Server B is connected to Server A as an OpenVPN client. I can ping Server A from Server B when doing: ping 172.15.0.1

However, any endpoints (SIP phones) that have obtained IP from Server B DHCPd can not ping 172.15.0.1. Network 172.15.0.0/24 is simply unreachable to them. My thought was that upon succesful establish of the openvpn connection the routes will populate properly but it seems that any requests to 172.15.0.1 from an endpoint and NOT Server B hits eth0 which is of course wrong because of the deault 0.0.0.0 route maybe??!!

**I just need all the endpoints that obtain their IP from eth1 of Server B (openvpn client) to be able to reach Server A by pinging it through tun0 interface**

Note: I can't do: push "redirect-gateway def1" because it will make Server B unreachable as all Enpoints of Server B will point to Server A for ALL the traffic even the DHCP packets and obtaining IPs which is wrong as there is no DHCPd service installed on Server A. The DHCPd server is only on Server B and attached to Eth1.

I don't use any firewalls on both sides. I guess my only option is "netstat -rn" and "route add -net" but I am not sure how to fix this or what to put there in the "route add".

Your input is greatly appreciated.

---

### Post by SeijiSensei on 2010-09-21
First thing to check is whether IP forwarding is enabled in the kernel. In a Terminal, type "cat /proc/sys/net/ipv4/ip_forward".  If it's zero, then the kernel will not pass packets between interfaces regardless of the routing table.  

You can change it on-the-fly with the command "sudo echo '1' > /proc/sys/net/ipv4/ip_forward" but to change it permanently you need to edit /etc/sysctl.conf.  Find the lines that read 

```

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

``` 

and remove the hash mark from the second line.  Forwarding will then be enabled permanently.

If this doesn't do the trick, we'll probably need to look at your routing table on Server B.

(Forwarding is disabled by default in most distributions these days for security reasons.)

---

### Post by torontobc on 2010-09-21
Thanks for reply. Seems my problem was not taking advantage of ccd in server.conf of openvpn.

---

