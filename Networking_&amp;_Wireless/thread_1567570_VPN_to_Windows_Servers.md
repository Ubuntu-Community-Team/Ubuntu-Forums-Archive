---
title: "VPN to Windows Servers"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by ghetto2ivy on 2010-09-04
So I've tried every tutorial, created my own pon and poff configs, yelled at network manager for a few hours, and otherwise pulled my hair out on this one.

I want to connect from my laptop (lucid lynx) to my work's vpn (windows servers) so that I can control the machine by remote desktop. Step 1) get the vpn is causing my headaches.

The settings I have work on windows xp and on mac (snow leopard), but wont work on Ubuntu. 

Network manager says the vpn failed to start. The Syslog barks about an invalid gateway. 

Here's the full syslog output

```
Sep  4 00:28:46 stinky64 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Sep  4 00:28:46 stinky64 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2730
Sep  4 00:28:46 stinky64 NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Sep  4 00:28:46 stinky64 NetworkManager: <info>  VPN plugin state changed: 1
Sep  4 00:28:48 stinky64 NetworkManager: <info>  VPN plugin state changed: 3
Sep  4 00:28:48 stinky64 NetworkManager: <info>  VPN connection 'Pirnie' (Connect) reply received.
Sep  4 00:28:48 stinky64 NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'Pirnie' failed to connect: 'invalid gateway 'gateway''.
Sep  4 00:28:48 stinky64 NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Sep  4 00:28:48 stinky64 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Sep  4 00:29:01 stinky64 NetworkManager: <debug> [1283574541.001385] ensure_killed(): waiting for vpn service pid 2730 to exit
Sep  4 00:29:01 stinky64 NetworkManager: <debug> [1283574541.001494] ensure_killed(): vpn service pid 2730 cleaned up

```

I should note that the gateway is not called 'gateway' I actually put a value in it, but it always gives that message when connecting via network manager.

---

### Post by ghetto2ivy on 2010-09-09
Bump!

---

### Post by nito2721 on 2012-02-03
I know this is an old thread, but I read this thread a few times before finding my answer. Hopefully this helps someone in the future. Remove http:// and / from your server names.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/664453](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/664453)

---

### Post by ghetto2ivy on 2012-02-04
Thanks! I gave up and configured a virtualbox for my wife, but I'll try this next time I get the issue.

---

