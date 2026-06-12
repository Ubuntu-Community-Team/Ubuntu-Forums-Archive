---
title: "Setting up a transparent proxy on 11.04 server"
date: 2013-08-14
forum: Networking &amp; Wireless
---

### Post by bytesoup on 2013-08-14
Hi Folks,

I have a 11.04 server running here at home which acts as a web proxy, mpd server and a general file server. I got squid installed and working and added DansGuardian recently too.

Everything seems to be working ok, but I was interested when reading about transparent proxys as apparently you do not need to configure the proxy onto the client machines, which would be preferrable. Already one of my kids has figured out where to de-configure the proxy on his windows machine ;-)

So my server is on 192.168.0.11, the home router is on 192.168.0.1. My question is this, in all the information I read about transparent proxying, none of it seems to say how the packets get to the proxy. For this to happen the home router (which acts as a DHCP server too) would need to send the clients the default gateway address not of the router at 192.168.0.1 but of the proxy server at 192.168.0.11. 

So as most home routers don't have much in the way you can configure for DHCP, would I be right in assuming that in order to implement a trasnparent proxy as well as the squid and possible iptables configuration, I would also need to make the proxy server the DHCP server too and that all client machines would have the 192.168.0.11 ip as the default gateway?

---

### Post by papibe on 2013-08-14
Hi bytesoup.

Yes. I think you have the correct picture of where that would lead you, that is, when your main concern is not configure manually every client on your network.

Although most routers are not very configurable, a significant number of them can turn off DHCP.

Installing a service to provide DHCP on your server is not that complicated. You can go with the DHCP Server and DNS combo, or (just easier) DNSmasq.

If the router's DHCP can't be disable, you could add a second NIC for your server so that your LAN gets under one card, and use the other card to connect to the server. You would also need to install and configure DHCP and DNS services on your server.

Just some thoughts. Let us know if you need more help with that.
Regards.

---

### Post by bytesoup on 2013-08-15
Hi papibe, ok thanks for that. I thought as much. I think actually having DHCP on the server probably wont take up much resource anyway and will give me better control over DHCP reservation and lease times etc.

I actually make use of OpenDNS, its configured on the server under /etc/resolv.conf so my question would be if I configured a DHCP server would it be possible to configure the DHCP clients with the OpenDNS IP addresses as part of the client configuration? This would prevent me needing to configure the DNS servers on each client machine too.

---

### Post by SeijiSensei on 2013-08-15
Setting up a transparent proxy works best if it is running on the client workstations' default gateway.  If the gateway is running Linux with Squid configured for transparent proxying, you can add an iptables rule like this:

```
/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --to-ports 3128
```

This rule tells the kernel to send any HTTP (port 80) packets that would go out on eth0 (assuming that is the Internet-facing interface) to the server's local port 3128, the one Squid listens on by default.  Then all requests intended for a remote web server are pushed through the proxy.

You cannot proxy HTTPS through Squid this way without a [lot of work]("http://wiki.squid-cache.org/Features/SslBump").  You can control HTTPS usage by blocking outbound requests to port 443 using an iptables INPUT rule.

If your router's DHCP configuration tool lets you specify the default gateway for client workstations, then you could configure it to use the server's IP as the default gateway for all the clients, and tell the server to use the router as its default gateway.  Then all outbound traffic would pass through the server and HTTP requests intercepted.  Make sure you enable forwarding in /etc/sysctl.conf if you take this approach; read the comments in that file for details.

---

### Post by bytesoup on 2013-08-15
> **SeijiSensei said:**
> If your router's DHCP configuration tool lets you specify the default gateway for client workstations...

Unfortunately it doesn't so I've had to configure the machine to run a DHCP server (isc-dhcp-server). However it seems that even though I have configured a nameserver in the /etc/dhcp/dhcpd.conf file  it doesn't seem to be propogating down to the clients. I can see the DHCP Request, ack etc in the /var/log/syslog of the server and the clients get a IP address, but no DNS in the /etc/resolv.conf file.

I need to try and figure this last bit out and then I'll have to solution I need.

By the way thanks for the IP tables rule, Im running dansguardian though to I will use the port 8080 to forward to:

/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --to-ports 8080

---

### Post by bytesoup on 2013-08-15
Im going to mark this thread as solved as I have everything working now:

I put my nameserver line into the subnet part of the dhcpd.conf file:

```
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.10 192.168.0.254;
  option routers 192.168.0.11;
  option broadcast-address 192.168.0.255;
  option domain-name-servers 208.67.220.220, 208.67.222.222;
}

```
Restarted the DHCP server

```
sudo service isc-dhcp-server restart
```

Added the iptables rule (im using dansguardian on port 8080 which forwards to squid on 3128):

```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
```

Then made sure ip forwarding was on:

```
sudo vi /etc/sysctl.conf
```

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```
Re-read sysctl

```
sudo sysctl -p /etc/sysctl.conf

```



Restarted the DHCP server just to be sure

```
sudo service isc-dhcp-server restart
```

Things seem to be working ok, clients are showing Open DNS in the /etc/resolv.conf and the DanGuardian block pages show up. All I need to do now is tweak things in dansguardian so i have things the way I want them

Thanks to you guys who helped out here!

---

### Post by Mandy_Bradshaw on 2013-08-15
Thanks for the help, guys! I had the same problem. Now, it's ok.

---

### Post by rajhanschinmay on 2013-09-02
I am on a network that uses proxy with authentication scheme.
Can anyone help me edit the conf file.

When I tried installing squid in Ubuntu 12.04, it automatically installed squid, squid3 and squid-common.

so let me know how to edit its conf file.

Thank you in advance.

---

