---
title: "VPN Setup"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by mocka on 2009-09-24
I have now tried to set up a VPN connection between my home LAN and any remote networks. My purpose is to use Samba to access workgroup shares is my home LAN from other remote places. 

Connection between remote client and my OpenVPN server is working perfectly fine. Although I cannot ping (at least not the normal way, but how do I differenciate between my current LAN and remote LAN?) neither can I access any Workgroup shares. I can see the Workgroup anyhow.

My network looks like this:
[IMG]http://i494.photobucket.com/albums/rr301/0control/Screenshots/mynetwork.png[/IMG]

Does anyone have any ideas what I might be doing wrong? Is my largest fear (that my server have to work as a gateway, ie. all computers must be connected to the server; instead of the router) true?

---

### Post by sedawk on 2009-09-24
I assume you create a point-to-point VPN between the remote
client and the "vpn server".

Two hints:
* Your VPN server has two IPS, the local IP and the
  VPN-IP. Pinging the VPN-IP should work.
  Pinging the VPN servers local IP might not work (see below)
* You might have to setup routing on your remote client,
  e.g. you have to tell it that IPs for the clients
  (or the local IP of the VPN server)
  have to travel via the VPN connection (gateway should
  be the VPN-IP of the VPN server).
* the VPN server receives the packages for the local clients
  (or his own local IP)  on his (virtual) VPN-interface, but
  if you do not enable IP forwarding, he is not allowed to
  send them to the right destination.
  (Turning on IP forwarding will turn your VPN server in
   some kind of router).
* You do not have to recable anything.
  
Check out some VPN tutorials. Is is easier to understand
if you see some examples and pictures and real network
addresses.

---

### Post by OfficeLinebacker on 2009-10-10
This is exactly what I'm going to be trying to do.  I'm doing some research now and OP is the first I've come across that clearly describes the network topology I am thinking of implementing.

I assume that it's a matter of configuring the router to forward a certain port to the VPN server?

In my case the VPN server is also a file server, and I wish only to be able to map a drive to the Samba share on the server, same as if the client was in the office.

Just want to say thanks for posting that image, to clarify exactly what we're talking about here.

---

