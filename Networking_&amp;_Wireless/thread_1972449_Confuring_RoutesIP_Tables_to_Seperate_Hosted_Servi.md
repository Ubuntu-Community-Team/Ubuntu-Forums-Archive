---
title: "Confuring Routes/IP Tables to Seperate Hosted Services From VPN Tunnel"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by l8knight on 2012-05-03
I have a headless Ubuntu server hosting website and a couple other services but I'd also like to connect the box to a VPN, without disrupting those services. I've been looking for some tutorials for configuring Routing and IPTables to accommodate this but everything I seem to find talks about connecting to your website via VPN, which is NOT what I want. 
Again, I'd like my website, ssh, etc to remain available by my public IP but all other traffic to go ONLY through the VPN tunnel.
 
Any help is appreciated and I thank you in advance!

---

### Post by SeijiSensei on 2012-05-03
"All other traffic" is probably not possible.  For instance, if I send an HTTP request to your web server, the server will reply using the same interface as the one I connected to.  Any other solution is convoluted and difficult to implement.

Let's start with asking what specifically you want to use a VPN for.  I have virtual machines on boxes that host websites using the public IPs and run VPNs back to my local office network.  Is that the kind of situation you're envisioning when you write:

> I'd like my website, ssh, etc to remain available by my public IP but all other traffic to go ONLY through the VPN tunnel.

What do you intend to use as the destination for the VPN? Can you describe a specific application that you'd like to implement?

---

### Post by l8knight on 2012-05-03
So if I want web, SSH and smtp to remain publicly accessible while traffic on specific ports (incoming/outgoing) would only use the VPN? For example, traffic on ports 4000-4100 or 9000-9100?
 
I am going to use OpenVPN to connect to the VPN, by the way.  I only have a single NIC in the Ubuntu Server, otherwise I'd seperate everything over two NICs.

---

### Post by SeijiSensei on 2012-05-03
What are you connecting with?  Some random machine somewhere on the Internet?  You can push all the traffic from the client through the tunnel to the remote server if you have some careful routing rules.

What you need to do is create a route from the client to the server's public IP via the client's ordinary default gateway.  Then once that route is established you can start the VPN tunnel and make the client's default gateway be the other end of the tunnel on the server.  Something like this:

Let's suppose the client machine is connected and normally uses a default gateway of 192.168.1.1.  Also let's assume that you have OpenVPN configured to create a tunnel with address 10.0.0.1 at the server end and 10.0.0.2 on the client.  Finally assume that the remote server has the public address 172.16.0.1.  Once the client is connected normally, you could run this series of commands:

```

#!/bin/bash
# script to repoint default gateway over OpenVPN

# set these as appropriate
VPNSERVER=172.16.0.1
TUNNELGW=10.0.0.1

# get my current default gateway
MYGATEWAY=$(ip route | grep default | awk '{print $3}')

# create a route to the VPN server that uses my default gateway
/sbin/ip route add "$VPNSERVER/32" via $MYGATEWAY

# start OpenVPN
/sbin/service openvpn start

# repoint my default gateway to the tunnel server's VPN IP
/sbin/ip route del default via $MYGATEWAY
/sbin/ip route add default via $TUNNELGW

```

If you save this as a script, mark it executable and run it with sudo.  If you type the individual commands in separately, you'll need to use sudo in all cases.  The first line gets your default gateway address automatically by parsing the "default" line returned by the command "ip route". In the example here, MYGATEWAY would be assigned the string "192.168.1.1".

Now your client machine can still see the remote server at 172.16.0.1 over the public Internet, but all other traffic will be pushed over the VPN to 10.0.0.1.

---

### Post by l8knight on 2012-05-03
Okay, thats a good start.  I'll try to get this going tonight and post back my results.  Thanks for getting me heading in the right direction!

---

