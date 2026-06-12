---
title: "Periodic VPN Disconnects"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by TSS on 2009-02-04
I'm using network-manager-pptp to connect to my VPN network.  Everything works great, except I experience frequent disconnects and I'm not sure why.  I've reproduced the relevant part of /var/log/daemon.log below.

```

1770 Feb  4 12:12:43 wall pptp[6087]: nm-pptp-service-6063 log[pptp_handle_timer:pptp_ctrl.c:1050]: closing control connection due to missing echo repl     y
1771 Feb  4 12:12:43 wall pptp[6087]: nm-pptp-service-6063 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
1772 Feb  4 12:12:43 wall pptp[6087]: nm-pptp-service-6063 log[pptp_conn_close:pptp_ctrl.c:430]: Closing PPTP connection
1773 Feb  4 12:12:43 wall pptp[6087]: nm-pptp-service-6063 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 3 'Stop-Control-Connection-Reque     st'
1774 Feb  4 12:12:43 wall pptp[6087]: nm-pptp-service-6063 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
1775 Feb  4 12:12:43 wall NetworkManager: <info>  VPN plugin failed: 1
1776 Feb  4 12:12:43 wall NetworkManager: <info>  VPN plugin state changed: 6
1777 Feb  4 12:12:43 wall NetworkManager: <info>  VPN plugin state change reason: 0
1778 Feb  4 12:12:43 wall NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
1779 Feb  4 12:12:43 wall NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
1780 Feb  4 12:12:43 wall NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
1781 Feb  4 12:12:43 wall avahi-daemon[4942]: Withdrawing address record for 192.17.199.212 on eth1.

```

I'd appreciate any help in interpreting these errors!

---

