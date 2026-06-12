---
title: "From internal network to vpn client"
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by jay_smith2 on 2013-07-31
Hello,

is it posible to connect(ssh or anything else) from an internal computer(is in the same net as the vpn server) to an vpn client?
Not each computer should be a vpn client.

Thanks!

---

### Post by TheFu on 2013-07-31
If I understand the question, the answer is yes, but dependent on the VPN configuration, client firewall, and client services.

If the client is not running the ssh-server, then no way.

If the VPN configuration doesn't allow reverse networking, then no way.  Usually, a VPN client will provide a DHCP IP on the remote LAN that can be accessed.  Since you are already using a VPN, using ssh isn't needed from a security perspective, but it is the way that I'd do it due to the connection simplicity and other features.

I know of a business that remotely manages servers using reverse ssh connections from the client site, so I know that is possible.  I've never tried it myself - it should work. I think there were some issues, but can't recall exactly what my friend did to overcome them. Sorry.

Interesting problem. Thanks for posting.  

Hopefully, someone with direct experience will post a solution. Can't wait to read it!

---

### Post by jay_smith2 on 2013-07-31
Thanks for your reply. This is exactly what i want.
I thought i can setting a route on my client where the default gateway is the ip(eth0 not tun0) of vpn server but this didn't works. Or i did it wrong.
Because i am able to ping my vpn clients from the vpn server machine.

Gateway: 192.168.122.2
Network: 192.168.122.0
VPN: 10.0.0.0

I set the default route as follow:
route add default -net 255.255.255.0 gw 192.168.122.2

Attention: The VPN server is in a vm.

---

### Post by TheFu on 2013-07-31
That is interesting missing the most important information - the remote, VPN client, IP address. Without that, you'll never get any connection. If you know the DHCP range provided by the VPN, you could search by IP for each client you want to connect.

We need to be very clear about "LAN-client", "VPN-client", "VPN-gateway" and normal "Gateway" in these discussions.

---

### Post by jay_smith2 on 2013-07-31
VPN Server:
eth0: 192.168.122.2
The normal gateway is 192.168.122.2 -> eth0 is a nat device on virtual machine. The ip address of virtual machines host is 192.168.122.1
tun0: 10.0.0.1
The VPN gateway is 10.0.0.2

Normal Client within the network:
eth0: 192.168.122.161

VPN Client outside the network
tun0: 10.0.0.3

---

### Post by TheFu on 2013-07-31
So, is the VPN client running an ssh-server?
Do you have an account on the remote VPN client?
Can you ssh to it by ssh user@10.0.0.3?

I'd think that the most you'd need to do is add the 10.0.0.0/24 network gateway to your network settings, if even that. If that doens't work, can you ping the VPN gateway at all?

---

