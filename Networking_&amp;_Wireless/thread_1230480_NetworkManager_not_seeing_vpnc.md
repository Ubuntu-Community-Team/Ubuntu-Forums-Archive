---
title: "NetworkManager not seeing vpnc"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by user111970 on 2009-08-03
I installed updates over the weekend and now the NetworkManager cannot see the vpnc plugin. It was working just fine before the updates. 

I have:
network-manager-vpnc 0.7.1~rc4.20090316+bzr21-0ubuntu2
vpnc 0.5.3-1

This is what I see in syslog:

Aug  3 10:36:20 mylaptop NetworkManager: <WARN>  impl_manager_activate_connection(): Connection (2) /org/freedesktop/NetworkManagerSettings/0 failed to activate: (2) The VPN service was invalid.

---

### Post by user111970 on 2009-08-03
Ok fixed. I had to apt-get purge network-manager-vpnc and install. 

apt-get remove network-manager-vpnc and installing didn't work. I guess some of the packages/dependencies might have been corrupted.

---

