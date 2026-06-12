---
title: "Run command to use network interface/adapter"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by ionoff on 2009-04-21
Is there a wrapper program, cmd, evn var, or whatever else that allows you to bind a command that is not interface aware to a specific network interface/adapter.

Aka, I have multiple IP's and want to do different network calls through different ip's on applications that do not know how to pick adapters.

For example, I may have eth0, eth0:1, eth0:2, eth1, eth2.

If it involves making the session (screen, bash, whatever) use an adapter by default, that is fine.

I don't want to globally make changes to the system, as I may have multiple processes running each on different adapters/ips.

I know I can use virtualization and some of the new kernel network isolation virtualization modes, but I am looking at doing it on a more per session/application basis.

I know I can add routes to specific ip's to bind to adapters, but I need to bind connections to the same source sometimes.  Also the IP or subdomain may not be known in advanced.

Another situation would be having one or more VPN's and wanting to pick the route to use for the instance.

---

