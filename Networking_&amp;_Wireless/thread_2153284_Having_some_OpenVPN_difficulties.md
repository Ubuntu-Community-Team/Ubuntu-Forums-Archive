---
title: "Having some OpenVPN difficulties"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by void.pointer on 2013-06-10
First of all, I am relatively new to Linux so I've been reading articles & stuff online, learning as I go.


I have an OpenVPN server running on my Ubuntu VPS host. For the most part, it seems to be working fine. On my Windows 7 machine, I am using the OpenVPN GUI client to connect to it. My server config does not push "redirect-gateway def1", this way I can selectively choose how each client will tunnel through the VPN.


In the case of my Windows machine, I do not allow the VPN adapter to tunnel internet traffic. I have a privoxy server running and listening on 10.8.0.1 (default VPN gateway). I tell my Chrome browser to connect to the proxy, which tunnels through the VPN.


I notice on rare occasions there are some URLS that just don't work. Here is one that doesn't:
[https://server.iad.liveperson.net/hc/51964021/?cmd=file&file=visitorWantsToChat&site=51964021&byhref=1&imageUrl=http://www.wm.com/wm/images&SESSIONVAR!skill=K00185](https://server.iad.liveperson.net/hc/51964021/?cmd=file&file=visitorWantsToChat&site=51964021&byhref=1&imageUrl=http://www.wm.com/wm/images&SESSIONVAR!skill=K00185)


This is a link for Live Chat over at the Waste Management website. The page immediately fails to load with:
Error 111 (net::ERR_TUNNEL_CONNECTION_FAILED): Unknown error.


Is this a server or client configuration issue? Anyone know why this isn't working? I have attached my server config and client configs, for any interested.


I also use OpenVPN Connect on my two rooted Android devices (Nexus 10 and Note II). Neither of these devices are able to connect to the internet for anything with the VPN on (Both of these devices *do* specify "redirect-gateway def1", I do not use the proxy on them). Other than that, they share the same OpenVPN configuration and certs/keys as the desktop client. While I do share the same certs/keys between 4 simultaneous connections, I have the "duplicate-cn" option enabled on my VPN server.

---

### Post by void.pointer on 2013-06-10
So I found out the problem. I rebooted my server and my iptables got reset. Doh! I google searched and found a few ways to make my iptables persistent, so I did that and it works great now. That solves the problem with my Android devices.

However, that URL still isn't working. When I turn off the VPN tunnel and use a direct connection, the URL works fine. Strange.

---

