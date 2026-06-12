---
title: "PPTP VPN connects via NM but goes down during SSH connection"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by andreaolivato on 2012-12-12
Hello,

I setup a VPN PPTP connection via network manager and it connects correctly (I see the lock near the notification icon and the message "Vpn connection has been successfully...")

As soon as I try to perform any SSH connection via the established tunnel the connection itself goes down with the message "Vpn connection failed".

the SSH connection always fails at 
```
debug1: SSH2_MSG_KEXINIT sent
```

I've looked into the system logs and this is the log

```
Dec 12 12:25:00 ushuaia NetworkManager[1155]: <info> Starting VPN service 'pptp'...
Dec 12 12:25:00 ushuaia NetworkManager[1155]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 7093
Dec 12 12:25:00 ushuaia NetworkManager[1155]: <info> VPN service 'pptp' appeared; activating connections
Dec 12 12:25:00 ushuaia NetworkManager[1155]: <info> VPN plugin state changed: init (1)
Dec 12 12:25:00 ushuaia NetworkManager[1155]: <info> VPN plugin state changed: starting (3)
Dec 12 12:25:00 ushuaia NetworkManager[1155]: <info> VPN connection 'Redation' (Connect) reply received.
Dec 12 12:25:05 ushuaia NetworkManager[1155]: <info> VPN connection 'Redation' (IP4 Config Get) reply received from old-style plugin.
Dec 12 12:25:05 ushuaia NetworkManager[1155]: <info> VPN Gateway: 5.98.141.210
Dec 12 12:25:06 ushuaia NetworkManager[1155]: <info> VPN connection 'Redation' (IP Config Get) complete.
Dec 12 12:25:06 ushuaia NetworkManager[1155]: <info> VPN plugin state changed: started (4)
Dec 12 12:25:14 ushuaia NetworkManager[1155]: <info> VPN plugin state changed: stopping (5)
Dec 12 12:25:14 ushuaia NetworkManager[1155]: <info> VPN plugin state changed: stopped (6)
Dec 12 12:25:14 ushuaia NetworkManager[1155]: <info> VPN plugin state change reason: 0
Dec 12 12:25:15 ushuaia NetworkManager[1155]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Dec 12 12:25:20 ushuaia NetworkManager[1155]: <info> VPN service 'pptp' disappeared
```

Please note that the same vpn is configured on my colleagues Windows 7 and works without problem when they use putty to connect via SSH

---

