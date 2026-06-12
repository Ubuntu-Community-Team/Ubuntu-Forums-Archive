---
title: "NetworkManager founds no networks"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by yaggo on 2006-05-31
If you are running NetworkManager but it does not found any networks or even network devices, this may be a quick solution:

$ sudo apt-get install hal

I have one machine dist-upgraded Debian -> Breezy -> Dapper and another machine running Breezy -> Dapper. Both of them had same problem: NetworkManager found no networks:

$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        main (): nm_data_new: Setting up dbus filter
NetworkManager: <information>   Updating allowed wireless network lists.
NetworkManager: <WARNING>        nm_dbus_get_networks_cb (): nm-dbus-nmi.c:522 (nm_dbus_get_networks_cb): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks.

Knetworkmanager also reported "No devices found".

So, all I had to do was install hal. Don't know why it didn't get installed when I dist-upgraded.

---

### Post by fastly on 2006-05-31
NetworkManager can't seem to find my wireless networks. Any ideas are greatly appreciated!

See output:

root@ubuntu:~# NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        nm_dbus_init (): nm_dbus_init() could not acquire the NetworkManager service as it is already taken (ret=3). Is the daemon already running?NetworkManager: <ERROR> [1149121802.497153] main (): nm_dbus_init() failed, exiting. Either dbus is not running, or the NetworkManager dbus security policy was not loaded.
NetworkManager: traceback:
NetworkManager:         NetworkManager(main+0x3e3) [0x8066ea8]
NetworkManager:         /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7caeea2]
NetworkManager:         NetworkManager [0x8052d91]
Trace/breakpoint trap

EDIT: forgot to mention, i have also just dist-upgraded from breezy to dapper... I tried yaggo's hal suggestion above. I'm running NetworkManage 0.6.2

---

