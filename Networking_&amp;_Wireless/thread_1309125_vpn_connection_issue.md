---
title: "vpn connection issue"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by palexv on 2009-11-01
Hi guys! 9.10 version is impressive, but need your help to resolve one issue I have.

I have internet connection via Wireless and everything is fine with this.

Also I need to connect to VPN. When I am trying to connect using build-in NetworkManager I see following in logs:


```
VPN plugin state changed: 3
VPN connection 'imstrac' (Connect) reply received.
kernel    [ 7969.630239] tun0: Disabled Privacy Extensions
NetworkManager       SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
NetworkManager       SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
NetworkManager       SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
NetworkManager    <info>  VPN plugin failed: 0
NetworkManager    <info>  VPN plugin state changed: 6
NetworkManager    <info>  VPN plugin state change reason: 10
NetworkManager    <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
NetworkManager    <info>  Policy set 'XATA' (wlan0) as default for routing and DNS.
```So connection does not up. Any ideas why? May be need modify /etc/network/interfaces ? I dont jnow what needs to be here.

In /etc/network/interfaces I have default values like 

```
auto lo
iface lo inet loopback
```Any suggestions?

---

### Post by Kimm on 2009-11-02
This is a known bug in KDE4, to connect using a VPN you need to use the network manager from Gnome.

To get it, install these packages (assuming its a PPTP VPN):
network-manager-gnome, network-manager-pptp

then run "nm-applet" in KDE.

---

### Post by palexv on 2009-11-03
> **Kimm said:**
> This is a known bug in KDE4, to connect using a VPN you need to use the network manager from Gnome.

To get it, install these packages (assuming its a PPTP VPN):
network-manager-gnome, network-manager-pptp

then run "nm-applet" in KDE.


Thanks you! It works!!!

---

### Post by infecticide on 2009-11-20
i have installed nm-applet however it seems KNetworkManager has the NetworkManager system on hold for itself:

```
** (nm-applet:3716): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3
```

How do you get around this?

---

### Post by Bytesource on 2009-12-05
I have exactly the same problem. I installed network-manager-gnome to replace knetworkmanager, but when trying to start nm-applet I get the *service as it is already taken* warning. 

I have the following questions:
1) How do I disable knetworkmanager(I don't want to uninstall it at the moment)
2) How do I make nm-applet start at boot?

Thanks in advance!

Stefan

---

### Post by Bytesource on 2009-12-05
I have exactly the same problem. I installed network-manager-gnome to replace knetworkmanager, but when trying to start nm-applet I get the "service as it is already taken" warning. 

Now I have the following question:
-- How do I disable knetworkmanager (I don't want to uninstall it at the moment)

Thanks in advance!

Stefan

---

### Post by Bytesource on 2009-12-06
Disabling KNetworkmanager to replace it with network-manager-gnome should be an easy task to do. However, as I haven't done this before I am afraid I'd end up with no network manager at all. 

Therefore I am still in need of some advice of how to securely disable KNetworkmanager and to use network-manager-gnome (nm-applet) instead.

Again, thank you very much in advance!

Stefan

---

