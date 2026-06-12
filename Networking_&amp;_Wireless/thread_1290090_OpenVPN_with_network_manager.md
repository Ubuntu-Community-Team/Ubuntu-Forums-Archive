---
title: "OpenVPN with network manager"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by brad_richards on 2009-10-13
I have a small mystery regarding OpenVPN - I hope some guru out there can help. Here's the situation:

I want to establish a VPN for use by a single client. The server runs OpenVPN 1.6; the client is Ubuntu 9.04. I am able to establish a VPN connection using either a static key or using TLS, as long as I start OpenVPN (on the client) in a terminal window.

The network manager cannot create an OpenVPN connection using a static key - this is a known bug. However, it *ought* to be able to create a TLS-session. What happens is: the server notes "Peer Connection Initiated", and seems happy. On the client, the network manager reports the following error in syslog:

*VPN connection 'connection-name' (IP Config Get) timeout exceeded*

I am at a loss as to what the problem is and how to fix it. Here is the configuration that works when I start OpenVPN from the command line:

```
dev tun
remote 123.456.78.90
ifconfig 192.168.2.1 192.168.2.254
up ./route.up
tls-client
ca ca.crt
cert client.cert
key client.key
port 5000
verb 3
```The contents of route.up are

```
route add -net 192.168.2.0 netmask 255.255.255.0 gw $5
```Again, this all works fine when started from the command line. The problem comes when I try to replicate these settings in the network-manager. I have been unable to find any useful information about the error message regarding "IP Config Get".

Can anyone give me an idea what the problem could be?

---

### Post by bonne1 on 2012-07-17
> **brad_richards said:**
> 
 
The network manager cannot create an OpenVPN connection using a static key - this is a known bug. However, it *ought* to be able to create a TLS-session. What happens is: the server notes "Peer Connection Initiated", and seems happy. On the client, the network manager reports the following error in syslog:
 
*VPN connection 'connection-name' (IP Config Get) timeout exceeded*
 
I am at a loss as to what the problem is and how to fix it. Here is the configuration that works when I start OpenVPN from the command line:
 

 
Did you manage to solve your problem?
 
I am having the same problem. a terminal "openvpn connection.ovpn" brings up the tunnel, but when the same ovpn file is imported in network manager, I also get a time out.
 
An even more odd finding is, that if I am creating the connection from scratch (not using the ovpn file, but entering IP addresses, pointing out cert and key files), network manager can't find my client.key file. I have even tried to give full access to world to this file, but it is not listed in the file window when trying to point out the file during the "configure VPN"-guide in network manager.
 
I worked ealier on this installation, but after upgrading firewall and reissuing easy-rsa files, it no longer works (other than through commandline"...
 
Anyone?
 
Regards, Lars.

---

