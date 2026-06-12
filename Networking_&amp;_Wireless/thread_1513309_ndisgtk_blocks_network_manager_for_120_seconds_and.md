---
title: "ndisgtk blocks network manager for 120 seconds and causes stack trace"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by tpeelen on 2010-06-19
I've troubles getting my new Sweex wireless 300N USB adapter to work. Tried searching in several directions (see [closed thread]("http://ubuntuforums.org/showthread.php?t=1512533")).

Further investigations shows however it is caused by the NDISGTK wrapper for Windows drivers. Can anyone tell me whether Sweex is shipping a faulty driver (it is the latest available) or it is a fault in ndisgtk? Or maybe I'm doing something stupid myself, which I do not find completely imagenary ;-) 

Anywhay below some more detailed information on my findings:

[LIST]
[*]Started with network off and examined the networkstatus
> 
tpeelen@CC-desktop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:5c:8a:be
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:e800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8fe0000-f8feffff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
tpeelen@CC-desktop:~$

[*]Continued by clicking the network on through the Gnome network applet which resulted in the following syslog
> 
Jun 19 15:27:10 CC-desktop NetworkManager: <info>  Waking up...
Jun 19 15:27:10 CC-desktop NetworkManager: <info>  (eth0): now managed
Jun 19 15:27:10 CC-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun 19 15:27:10 CC-desktop NetworkManager: <info>  (eth0): bringing up device.
Jun 19 15:27:10 CC-desktop NetworkManager: <info>  (eth0): preparing device.
Jun 19 15:27:10 CC-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun 19 15:27:10 CC-desktop kernel: [ 1136.015986] r8169: eth0: link down
Jun 19 15:27:10 CC-desktop kernel: [ 1136.016832] ADDRCONF(NETDEV_UP): eth0: link is not ready

[*]Installed the XP 64bit driver from Sweex, lw3x3_xpx64.inf, through ndisgtk
> 
Jun 19 15:30:32 CC-desktop kernel: [ 1337.391345] usbcore: deregistering interface driver ndiswrapper
Jun 19 15:30:32 CC-desktop kernel: [ 1337.402558] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jun 19 15:30:32 CC-desktop kernel: [ 1337.407700] usbcore: registered new interface driver ndiswrapper

[*]inserting the physical adapter itself into the USB-slot seemed to go allright
> 
Jun 19 15:32:50 CC-desktop kernel: [ 1475.980013] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun 19 15:32:50 CC-desktop kernel: [ 1476.148309] usb 2-1: configuration #1 chosen from 1 choice
Jun 19 15:32:51 CC-desktop kernel: [ 1476.280017] usb 2-1: reset high speed USB device using ehci_hcd and address 2
Jun 19 15:32:51 CC-desktop kernel: [ 1476.443784] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Jun 19 15:32:51 CC-desktop kernel: [ 1476.446175] ndiswrapper: driver lw3x3_xpx64 (Sweex,08/13/2009, 1.04.05.0000) loaded
Jun 19 15:32:51 CC-desktop kernel: [ 1477.070857] wlan0: ethernet device 00:16:0a:20:5d:dd using NDIS driver: lw3x3_xpx64, version: 0x0, NDIS version: 0x501, vendor: 'IEEE 802.11 Wireless Card.', 177F:0313.F.conf
Jun 19 15:32:51 CC-desktop kernel: [ 1477.070881] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jun 19 15:32:51 CC-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/net/wlan0, iface: wlan0)
Jun 19 15:32:51 CC-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): now managed
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): bringing up device.
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): preparing device.
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jun 19 15:32:51 CC-desktop kernel: [ 1477.092999] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jun 19 15:32:51 CC-desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto ThomsonB0C183'
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto ThomsonB0C183' has security, but secrets are required.
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto ThomsonB0C183' has security, and secrets exist.  No new secrets needed.
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Config: added 'ssid' value 'ThomsonB0C183'
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jun 19 15:32:56 CC-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 19 15:32:56 CC-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Jun 19 15:32:56 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jun 19 15:33:01 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun 19 15:33:06 CC-desktop wpa_supplicant[992]: Trying to associate with b4:82:fe:b0:c1:83 (SSID='ThomsonB0C183' freq=2437 MHz)
Jun 19 15:33:06 CC-desktop wpa_supplicant[992]: Association request to the driver failed
Jun 19 15:33:06 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun 19 15:33:06 CC-desktop kernel: [ 1492.166784] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Jun 19 15:33:06 CC-desktop wpa_supplicant[992]: Associated with b4:82:fe:b0:c1:83
Jun 19 15:33:06 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jun 19 15:33:06 CC-desktop kernel: [ 1492.242516] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 19 15:33:07 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jun 19 15:33:08 CC-desktop avahi-daemon[856]: Registering new address record for fe80::216:aff:fe20:5ddd on wlan0.*.
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jun 19 15:33:08 CC-desktop wpa_supplicant[992]: WPA: Key negotiation completed with b4:82:fe:b0:c1:83 [PTK=CCMP GTK=TKIP]
Jun 19 15:33:08 CC-desktop wpa_supplicant[992]: CTRL-EVENT-CONNECTED - Connection to b4:82:fe:b0:c1:83 completed (auth) [id=0 id_str=]
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ThomsonB0C183'.
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  dhclient started with pid 2286
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun 19 15:33:08 CC-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun 19 15:33:08 CC-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun 19 15:33:08 CC-desktop dhclient: All rights reserved.
Jun 19 15:33:08 CC-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jun 19 15:33:08 CC-desktop dhclient: 
Jun 19 15:33:08 CC-desktop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Jun 19 15:33:08 CC-desktop dhclient: Listening on LPF/wlan0/00:16:0a:20:5d:dd
Jun 19 15:33:08 CC-desktop dhclient: Sending on   LPF/wlan0/00:16:0a:20:5d:dd
Jun 19 15:33:08 CC-desktop dhclient: Sending on   Socket/fallback
Jun 19 15:33:09 CC-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jun 19 15:33:17 CC-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Jun 19 15:33:17 CC-desktop kernel: [ 1502.330005] wlan0: no IPv6 routers present
Jun 19 15:33:36 CC-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun 19 15:33:45 CC-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2286
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  Activation (wlan0) failed for access point (ThomsonB0C183)
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  Marking connection 'Auto ThomsonB0C183' invalid.
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  Activation (wlan0) failed.
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jun 19 15:33:53 CC-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

[*]Clicking on the gnome network applet resulted in a stack trace after 2 minutes
> 
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720020] INFO: task NetworkManager:857 blocked for more than 120 seconds.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720024] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720026] NetworkManage D 00000000ffffffff     0   857      1 0x00000000
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720031]  ffff8802235e1a58 0000000000000082 0000000000015bc0 0000000000015bc0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720036]  ffff8802330083c0 ffff8802235e1fd8 0000000000015bc0 ffff880233008000
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720039]  0000000000015bc0 ffff8802235e1fd8 0000000000015bc0 ffff8802330083c0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720044] Call Trace:
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720052]  [<ffffffff81542077>] __mutex_lock_slowpath+0xe7/0x170
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720056]  [<ffffffff81454f30>] ? __alloc_skb+0x80/0x190
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720059]  [<ffffffff81541f6b>] mutex_lock+0x2b/0x50
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720063]  [<ffffffff8146bf25>] rtnl_lock+0x15/0x20
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720066]  [<ffffffff8146bf46>] rtnetlink_rcv+0x16/0x40
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720070]  [<ffffffff8148308e>] netlink_unicast+0x2de/0x2f0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720073]  [<ffffffff81483e7e>] netlink_sendmsg+0x1fe/0x2e0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720077]  [<ffffffff8144df0b>] sock_sendmsg+0x10b/0x140
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720082]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720085]  [<ffffffff8144f450>] ? sock_aio_write+0x0/0x150
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720089]  [<ffffffff8144d464>] ? move_addr_to_kernel+0x64/0x70
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720092]  [<ffffffff81458669>] ? verify_iovec+0x69/0xc0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720095]  [<ffffffff8144e373>] sys_sendmsg+0x233/0x3a0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720099]  [<ffffffff81144922>] ? do_readv_writev+0x162/0x1f0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720103]  [<ffffffff811449f8>] ? vfs_writev+0x48/0x60
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720106]  [<ffffffff81144b72>] ? sys_writev+0xa2/0xb0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720110]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720120] INFO: task wpa_supplicant:992 blocked for more than 120 seconds.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720122] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720124] wpa_supplican D 00000000ffffffff     0   992      1 0x00000000
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720128]  ffff880223679c78 0000000000000082 0000000000015bc0 0000000000015bc0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720132]  ffff88023300c890 ffff880223679fd8 0000000000015bc0 ffff88023300c4d0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720135]  0000000000015bc0 ffff880223679fd8 0000000000015bc0 ffff88023300c890
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720139] Call Trace:
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720143]  [<ffffffff81542077>] __mutex_lock_slowpath+0xe7/0x170
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720147]  [<ffffffff81523190>] ? ioctl_standard_call+0x0/0xd0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720150]  [<ffffffff81541f6b>] mutex_lock+0x2b/0x50
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720153]  [<ffffffff8146bf25>] rtnl_lock+0x15/0x20
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720156]  [<ffffffff81522a49>] wext_ioctl_dispatch+0x59/0xb0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720159]  [<ffffffff81523570>] ? ioctl_private_call+0x0/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720162]  [<ffffffff81522bd6>] wext_handle_ioctl+0x46/0x90
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720166]  [<ffffffff8101c838>] ? save_i387_xstate+0x168/0x220
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720170]  [<ffffffff814623f3>] dev_ioctl+0x423/0x430
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720174]  [<ffffffff81143a6a>] ? do_sync_read+0xfa/0x140
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720177]  [<ffffffff8144c74d>] sock_ioctl+0x9d/0x280
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720181]  [<ffffffff81153cd2>] vfs_ioctl+0x22/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720185]  [<ffffffff81252326>] ? security_file_permission+0x16/0x20
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720188]  [<ffffffff81153f81>] do_vfs_ioctl+0x81/0x380
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720191]  [<ffffffff81144451>] ? vfs_read+0x181/0x1a0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720194]  [<ffffffff81012e65>] ? sys_rt_sigreturn+0x235/0x250
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720198]  [<ffffffff81154301>] sys_ioctl+0x81/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720201]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720210] INFO: task multiload-apple:1488 blocked for more than 120 seconds.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720212] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720214] multiload-app D 0000000000000000     0  1488      1 0x00000000
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720218]  ffff8802202c5b38 0000000000000086 0000000000015bc0 0000000000015bc0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720222]  ffff880234839ab0 ffff8802202c5fd8 0000000000015bc0 ffff8802348396f0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720225]  0000000000015bc0 ffff8802202c5fd8 0000000000015bc0 ffff880234839ab0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720229] Call Trace:
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720233]  [<ffffffff81542077>] __mutex_lock_slowpath+0xe7/0x170
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720237]  [<ffffffff810397a9>] ? default_spin_lock_flags+0x9/0x10
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720240]  [<ffffffff81541f6b>] mutex_lock+0x2b/0x50
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720258]  [<ffffffffa0bc5a9f>] mp_request+0x26f/0x3a0 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720262]  [<ffffffff81483e7e>] ? netlink_sendmsg+0x1fe/0x2e0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720265]  [<ffffffff81523570>] ? ioctl_private_call+0x0/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720275]  [<ffffffffa0bae449>] iw_get_network_type+0x39/0xb0 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720279]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720282]  [<ffffffff815231f0>] ioctl_standard_call+0x60/0xd0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720286]  [<ffffffff81461150>] ? __dev_get_by_name+0xa0/0xc0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720289]  [<ffffffff81523190>] ? ioctl_standard_call+0x0/0xd0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720292]  [<ffffffff81522969>] wireless_process_ioctl+0xe9/0x170
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720295]  [<ffffffff81523190>] ? ioctl_standard_call+0x0/0xd0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720298]  [<ffffffff81522a61>] wext_ioctl_dispatch+0x71/0xb0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720301]  [<ffffffff81523570>] ? ioctl_private_call+0x0/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720304]  [<ffffffff81522bd6>] wext_handle_ioctl+0x46/0x90
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720307]  [<ffffffff814613fa>] ? dev_ifsioc_locked+0x8a/0x1f0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720310]  [<ffffffff814623f3>] dev_ioctl+0x423/0x430
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720314]  [<ffffffff81451c58>] ? sk_prot_alloc+0x48/0x180
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720317]  [<ffffffff81252e26>] ? security_sk_alloc+0x16/0x20
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720320]  [<ffffffff8144c74d>] sock_ioctl+0x9d/0x280
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720324]  [<ffffffff81153cd2>] vfs_ioctl+0x22/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720327]  [<ffffffff8154356e>] ? _spin_lock+0xe/0x20
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720330]  [<ffffffff81141647>] ? fd_install+0x67/0x90
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720333]  [<ffffffff81153f81>] do_vfs_ioctl+0x81/0x380
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720336]  [<ffffffff8144cb9c>] ? sock_map_fd+0x4c/0x80
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720339]  [<ffffffff81154301>] sys_ioctl+0x81/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720342]  [<ffffffff8144d2b1>] ? sys_socket+0x51/0x80
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720346]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720353] INFO: task ntos_wq:2247 blocked for more than 120 seconds.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720355] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720357] ntos_wq       D ffff880028316730     0  2247      2 0x00000000
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720361]  ffff880214367c90 0000000000000046 0000000000015bc0 0000000000015bc0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720365]  ffff88020d5683c0 ffff880214367fd8 0000000000015bc0 ffff88020d568000
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720369]  0000000000015bc0 ffff880214367fd8 0000000000015bc0 ffff88020d5683c0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720373] Call Trace:
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720376]  [<ffffffff81542077>] __mutex_lock_slowpath+0xe7/0x170
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720380]  [<ffffffff8105b034>] ? try_to_wake_up+0x284/0x380
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720384]  [<ffffffff81541f6b>] mutex_lock+0x2b/0x50
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720399]  [<ffffffffa0bbe96a>] IoDequeueThreadIrp+0x9a/0x150 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720414]  [<ffffffffa0bbea3c>] IoFreeIrp+0x1c/0x30 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720429]  [<ffffffffa0bbeb5d>] IofCompleteRequest+0x10d/0x1c0 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720445]  [<ffffffffa0bc90d5>] wrap_urb_complete_worker+0xf5/0x1d0 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720460]  [<ffffffffa0bc8fe0>] ? wrap_urb_complete_worker+0x0/0x1d0 [ndiswrapper]
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720464]  [<ffffffff81080867>] run_workqueue+0xc7/0x1a0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720468]  [<ffffffff810809e3>] worker_thread+0xa3/0x110
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720471]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720474]  [<ffffffff81080940>] ? worker_thread+0x0/0x110
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720477]  [<ffffffff810850b6>] kthread+0x96/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720481]  [<ffffffff810141ea>] child_rip+0xa/0x20
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720484]  [<ffffffff81085020>] ? kthread+0x0/0xa0
Jun 19 15:36:15 CC-desktop kernel: [ 1680.720486]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[/LIST]

All help is appreciated. I'm lost!

---

### Post by tpeelen on 2010-06-25
In the end solved it myself by using this help [http://forum.ubuntu-nl.org/internet-en-draadloos/sweex-lw313/](http://forum.ubuntu-nl.org/internet-en-draadloos/sweex-lw313/) (Dutch language).

It comes down to the following:

- (in my case) uninstall ndisgtk and ndiswrapper completely and remove /etc/modprobe.d/ndiswrapper by hand
- check if the rt2800usb driver is installed
[INDENT]lsmod[/INDENT]
- If so then blacklist rt2800usb by creating the file /etc/modprobe.d/sweex-wireless-300n containing the following line:
[INDENT]blacklist rt2800usb[/INDENT]
- RT2870Sta drivers downloaden at Ralink: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) (it's the RT2870USB(RT2870/RT2770) driver)
- in my case I had to rename the extention to .tgz to be able to open it and extract it to /usr/src/....
- check the usb id of the device by using the following command, having the usb device plugged in and again after being removed; check the differences, it's the id you want to know
- Edit rtusb_dev_id.c and add your usb id (probably 1ff7,0313) 
- compile and install (sudo make, sudo make install)
- load the driver by
[INDENT]sudo /sbin/insmod os/linux/rt2870sta.ko[/INDENT]
- plug in your USB adapter
- sudo ifconfig ra0 up
- voila, it should work

---

