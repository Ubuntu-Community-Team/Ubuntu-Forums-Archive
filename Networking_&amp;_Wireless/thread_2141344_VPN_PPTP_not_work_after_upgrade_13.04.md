---
title: "VPN PPTP not work after upgrade 13.04"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by ITA003 on 2013-05-02
Hi!
I just upgrade ubuntu to 13.04 (from 12.10) and the VPN PPTP stop working with the message:

```
The VPN Connection 'VPN Connection 1' failed because the VPN service failed to start
```

I uninstall and reinstall all network-pptp package.
I deleted the keyrin in .gnome2/keyrings/

The syslog:

```
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> Starting VPN service 'pptp'...
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 17282
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> VPN service 'pptp' appeared; activating connections
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> VPN plugin state changed: init (1)
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> VPN plugin state changed: starting (3)
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> VPN connection 'VPN Connection 1' (Connect) reply received.
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <warn> VPN connection 'VPN Connection 1' failed to connect: 'Could not find the pppd binary.'.
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <info> Policy set 'Auto WIRELESS' (wlan0) as default for IPv4 routing and DNS.
May  2 17:09:26 xxxxxxxxxxx NetworkManager[14753]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
May  2 17:09:31 xxxxxxxxxxx NetworkManager[14753]: <info> VPN service 'pptp' disappeared

```

Any idea??

Thanks.

---

### Post by ITA003 on 2013-05-06
I opened a Bug requested:

[https://bugs.launchpad.net/ubuntu/+bug/1175897](https://bugs.launchpad.net/ubuntu/+bug/1175897)

---

