---
title: "Unable to Connect to UCLA VPN"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by Shadyabhi on 2010-02-19
I followed the [tutorial given here]("http://goo.gl/7DH0").

But, I am still not able to connect to the VPN, I get the messsage "The VPN Connection XXX failed through the libnotify..

The output of /var/log/syslog....

```
Feb 19 15:18:08 shadyabhi-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'...
Feb 19 15:18:08 shadyabhi-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 21980
Feb 19 15:18:08 shadyabhi-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections
Feb 19 15:18:08 shadyabhi-desktop NetworkManager: <info>  VPN plugin state changed: 1
Feb 19 15:18:17 shadyabhi-desktop NetworkManager: <info>  VPN plugin state changed: 3
Feb 19 15:18:17 shadyabhi-desktop NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Feb 19 15:18:17 shadyabhi-desktop kernel: [72262.365763] tun0: Disabled Privacy Extensions
Feb 19 15:18:17 shadyabhi-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Feb 19 15:18:17 shadyabhi-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Feb 19 15:18:20 shadyabhi-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Feb 19 15:18:20 shadyabhi-desktop NetworkManager: <info>  VPN plugin failed: 1
Feb 19 15:18:20 shadyabhi-desktop NetworkManager: <info>  VPN plugin state changed: 6
Feb 19 15:18:20 shadyabhi-desktop NetworkManager: <info>  VPN plugin state change reason: 0
Feb 19 15:18:20 shadyabhi-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Feb 19 15:18:20 shadyabhi-desktop NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Feb 19 15:18:20 shadyabhi-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Feb 19 15:18:33 shadyabhi-desktop NetworkManager: <debug> [1266572913.002459] ensure_killed(): waiting for vpn service pid 21980 to exit
Feb 19 15:18:33 shadyabhi-desktop NetworkManager: <debug> [1266572913.002563] ensure_killed(): vpn service pid 21980 cleaned up

```

I am sure that I am writing the correct password. What can be the problem? Also i came across a bug due to which "No VPN Secrets" was displayed, so now i always deny "Allow Application to access Keyrings"....

Guyz, pls help.. I am getting really frustrated.

---

### Post by Jamie Jackson on 2010-02-19
Do you know anybody else at the school who can access the gateway via NetworkManager? The reason I ask is my corp changed Cisco VPN gateways and the new one requires some obscure options that network-manager-vpn doesn't support. I've had to resort to using vpnc instead, like this:

```
sudo vpnc ~/Documents/mycorp.vpnc --local-port 0 --application-version "Cisco Systems VPN Client 0.3:WinNT"
```

Without those extra params, it's a no go. Not sure if this is your problem or not, but just realize that network-manager-vpnc only supports some of the more vanilla gateway configs.

---

### Post by Shadyabhi on 2010-02-25
Can you be more specific about how to give those options.
And I dont know if anybody else can access that VPN from my University.

---

