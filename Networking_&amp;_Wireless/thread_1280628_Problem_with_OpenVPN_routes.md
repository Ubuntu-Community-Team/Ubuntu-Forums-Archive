---
title: "Problem with OpenVPN routes"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by chx86 on 2009-10-02
I'm often on a very restriced network that uses DPI to limit what we may access. Basically most ports and services are locked down exept for HTTP to a few limited hostnames. I have written a a small program which encodes a TCP stream into multiple HTTP requests with spoofed Host-header, which the DPI allows to be sent out on the internet.

I've tried my program using SSH/Socks5 and it works fine, I am able to reach my home server. The problem starts when I try to use OpenVPN. Using OpenVPN without telling it to reroute all traffic on the VPN works fine, I am able to access my server. However when rerouting (using openvpns "redirect-gateway def1") the connection between my TCP proxy client and my proxy server times out. I believe this is because OpenVPN tries to route packets created by my proxy client out on the VPN interface, which is impossible by design.

Any ideas on how to solve this is appreciated. Strangely, this problem does not affect Windows Vista and Windows 7, they work both the way I want them to, my proxy client is able to talk to the server even after the VPN goes live and reroute the traffic. All linux distros I've tried, including Ubuntu, and Windows XP (and earlier) is however affected. Using OpenVPN on an unrestricted network without my proxy client works fine.

OpenVPN does connect and gets assigned an IP address when using my proxy server. It times out after having added the routes.

Here's some more information about how I've set things up:

**Client**
OpenVPN connects to 127.0.0.1:1100
My proxy clients listens on 127.0.0.1:1100
The proxy client makes a fake HTTP request to *homeserver.com*:80 for each TCP connection it accepts

**Home server**
OpenVPN listens on port 1194, all interfaces
My proxy server listens on port 80
When a client connects to port 80, my proxy server performs the fake HTTP handshake and then redirects the TCP stream to 127.0.0.1:1194

**Edit**
After doing some more testing and research, it looks like OpenVPN is adding a route to the ip address which is specified in the *remote *directive in the openvpn configuration file. As I use 127.0.0.1 as *remote* server, no such route to my home ip address is added, and therefor packets are sent out in the VPN tunnel instead. Still not sure why Vista decides to send them out using the physical ethernet port...

**Edit 2**
Used the *push* directive in OpenVPN to push a route to the client to my server. Works fine on all platforms now.

---

