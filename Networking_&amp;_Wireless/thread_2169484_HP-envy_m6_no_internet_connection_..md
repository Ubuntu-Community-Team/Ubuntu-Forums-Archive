---
title: "HP-envy m6 no internet connection ."
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by tahir2 on 2013-08-22
Hi guys ,

i am new to ubuntu i just installed ubuntu 12.04.2 desktop amd64 by bootable Usb . after installation its shows no available wifi networks and also not connecting with ethernet cable . i tried rfkill commands but doesn't work , in rfkill list all the fields are set to no .. but sometimes after restarting the wifi is hard blocked too . it is acting really weird . waiting for ur help guys

---

### Post by chili555 on 2013-08-22
Let's gather some information first. Please open a terminal and run and post:```
rfkill list all
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by tahir2 on 2013-08-22
rfkill list all0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
 lspci -nn | grep -e 0200 -e 0280
07:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
08:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)

and forgot to tell one thing it is installed alongside windows 8 in the same partition . i just used shrink drive option to create a partition within partition . which worked fine for linux mint 15 cinnamon .

---

### Post by chili555 on 2013-08-22
Since you mentioned ethernet in the original post, let's start there. The driver for your device is r8169. Is it loaded?```
lsmod | grep r8169
```Are there informative messages here? Firmware, by chance??```
dmesg | grep -e eth0 -e r8169 -e rtl
```Does it try to connect?

---

### Post by tahir2 on 2013-08-22
lsmod | grep r8169


r8169                  62766  0 




dmesg | grep -e eth0 -e r8169 -e rtfl




[    1.324973] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.325132] r8169 0000:07:00.2: irq 43 for MSI/MSI-X
[    1.325422] r8169 0000:07:00.2: eth0: RTL8411 at 0xffffc900117a6000, 84:34:97:18:b1:27, XID 08800800 IRQ 43
[    1.325425] r8169 0000:07:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   15.631203] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.216724] r8169 0000:07:00.2: eth0: link down
[   16.217158] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.217348] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

when i am connecting the ethernet it only shows connecting nothing else .. so wired and wireless bot aren't working

---

### Post by chili555 on 2013-08-22
Let's dig even deeper:```
nm-tool
cat /var/log/syslog | grep -e etwork -e eth0
```The wireless device is covered by the driver ath9k in Ubuntu 13.04 and later, not 12.04. Let's see if we can trick the ethernet to life before we address the wireless.

Of course, you could try the live CD for 13.04 and see if both devices are working.

---

### Post by tahir2 on 2013-08-22
nm-tool


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        84:34:97:18:B1:27


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




cat /var/log/syslog | grep -e etwork -e eth0




Aug 22 16:34:25 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.333657] r8169 0000:07:00.2: eth0: RTL8411 at 0xffffc900117a6000, 84:34:97:18:b1:27, XID 08800800 IRQ 43
Aug 22 16:34:25 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.333660] r8169 0000:07:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug 22 16:34:25 tahir-HP-ENVY-m6-Notebook-PC kernel: [    4.922682] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 16:34:27 tahir-HP-ENVY-m6-Notebook-PC kernel: [    8.807097] type=1400 audit(1377203667.317:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=717 comm="apparmor_parser"
Aug 22 16:34:27 tahir-HP-ENVY-m6-Notebook-PC kernel: [    8.807109] type=1400 audit(1377203667.317:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=671 comm="apparmor_parser"
Aug 22 16:34:27 tahir-HP-ENVY-m6-Notebook-PC avahi-daemon[841]: Network interface enumeration completed.
Aug 22 16:34:29 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 22 16:34:29 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 22 16:34:30 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 22 16:34:30 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> DNS: loaded plugin dnsmasq
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: init!
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: update_system_hostname
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPluginIfupdown: management mode: unmanaged
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0)
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: end _init.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    Ifupdown: get unmanaged devices count: 0
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: (40895280) ... get_connections.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    SCPlugin-Ifupdown: (40895280) ... get_connections (managed=false): return empty list.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]:    Ifupdown: get unmanaged devices count: 0
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> modem-manager is now available
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (driver hp-wmi)
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> Networking is enabled by state file
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): carrier is OFF
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): now managed
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 22 16:34:31 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): bringing up device.
Aug 22 16:34:32 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): preparing device.
Aug 22 16:34:32 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 22 16:34:32 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[903]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0
Aug 22 16:34:32 tahir-HP-ENVY-m6-Notebook-PC kernel: [   13.579271] r8169 0000:07:00.2: eth0: link down
Aug 22 16:34:32 tahir-HP-ENVY-m6-Notebook-PC kernel: [   13.579717] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 16:34:32 tahir-HP-ENVY-m6-Notebook-PC kernel: [   13.579940] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 16:34:36 tahir-HP-ENVY-m6-Notebook-PC kernel: [   17.592529] type=1400 audit(1377203676.113:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1010 comm="apparmor_parser"
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.380977] r8169 0000:07:00.2: eth0: RTL8411 at 0xffffc900117a6000, 84:34:97:18:b1:27, XID 08800800 IRQ 43
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.380980] r8169 0000:07:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   15.863981] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.106439] type=1400 audit(1377208155.618:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.106450] type=1400 audit(1377208155.618:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   50.761187] type=1400 audit(1377208190.310:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=909 comm="apparmor_parser"
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> DNS: loaded plugin dnsmasq
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: init!
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: update_system_hostname
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPluginIfupdown: management mode: unmanaged
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0)
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: end _init.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    Ifupdown: get unmanaged devices count: 0
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: (32177968) ... get_connections.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    SCPlugin-Ifupdown: (32177968) ... get_connections (managed=false): return empty list.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]:    Ifupdown: get unmanaged devices count: 0
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> modem-manager is now available
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (driver hp-wmi)
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> Networking is enabled by state file
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): carrier is OFF
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): now managed
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): bringing up device.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): preparing device.
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[929]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   50.906611] r8169 0000:07:00.2: eth0: link down
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   50.907192] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 17:49:50 tahir-HP-ENVY-m6-Notebook-PC kernel: [   50.907446] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 23:27:01 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.358195] r8169 0000:07:00.2: eth0: RTL8411 at 0xffffc900117a6000, 84:34:97:18:b1:27, XID 08800800 IRQ 43
Aug 22 23:27:01 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.358197] r8169 0000:07:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug 22 23:27:01 tahir-HP-ENVY-m6-Notebook-PC kernel: [   15.975147] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.633969] type=1400 audit(1377228422.160:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=582 comm="apparmor_parser"
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.731814] type=1400 audit(1377228422.260:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=827 comm="apparmor_parser"
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> DNS: loaded plugin dnsmasq
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: init!
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: update_system_hostname
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPluginIfupdown: management mode: unmanaged
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0)
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: end _init.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    Ifupdown: get unmanaged devices count: 0
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: (26119984) ... get_connections.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    SCPlugin-Ifupdown: (26119984) ... get_connections (managed=false): return empty list.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]:    Ifupdown: get unmanaged devices count: 0
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> modem-manager is now available
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> Networking is enabled by state file
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): carrier is OFF
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): now managed
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): bringing up device.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): preparing device.
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.888054] r8169 0000:07:00.2: eth0: link down
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.888658] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 23:27:02 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.888868] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 23:27:03 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[859]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (driver hp-wmi)
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.325422] r8169 0000:07:00.2: eth0: RTL8411 at 0xffffc900117a6000, 84:34:97:18:b1:27, XID 08800800 IRQ 43
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.325425] r8169 0000:07:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [   15.631203] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [   15.851778] type=1400 audit(1377232938.375:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> DNS: loaded plugin dnsmasq
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC avahi-daemon[870]: Network interface enumeration completed.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: init!
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: update_system_hostname
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPluginIfupdown: management mode: unmanaged
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0)
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: end _init.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    Ifupdown: get unmanaged devices count: 0
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: (10727216) ... get_connections.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    SCPlugin-Ifupdown: (10727216) ... get_connections (managed=false): return empty list.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]:    Ifupdown: get unmanaged devices count: 0
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> modem-manager is now available
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> Networking is enabled by state file
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): carrier is OFF
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): now managed
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): bringing up device.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): preparing device.
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.216724] r8169 0000:07:00.2: eth0: link down
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.217158] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 23 00:42:18 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.217348] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 23 00:42:19 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[880]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (driver hp-wmi)
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.348931] r8169 0000:07:00.2: eth0: RTL8411 at 0xffffc900117a6000, 84:34:97:18:b1:27, XID 08800800 IRQ 43
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [    1.348934] r8169 0000:07:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.219581] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.440503] type=1400 audit(1377266588.961:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [   16.440512] type=1400 audit(1377266588.961:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> DNS: loaded plugin dnsmasq
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: init!
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: update_system_hostname
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPluginIfupdown: management mode: unmanaged
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0)
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: end _init.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    Ifupdown: get unmanaged devices count: 0
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: (20827952) ... get_connections.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    SCPlugin-Ifupdown: (20827952) ... get_connections (managed=false): return empty list.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]:    Ifupdown: get unmanaged devices count: 0
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> modem-manager is now available
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> Networking is enabled by state file
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <warn> failed to allocate link cache: (-10) Operation not supported
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): carrier is OFF
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): now managed
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): bringing up device.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): preparing device.
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2/net/eth0
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [   17.003901] r8169 0000:07:00.2: eth0: link down
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [   17.004347] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC kernel: [   17.004533] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 23 10:03:09 tahir-HP-ENVY-m6-Notebook-PC NetworkManager[849]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (driver hp-wmi)

---

### Post by tahir2 on 2013-08-23
i've just plugged again my ethernet now its working fine and detecting the network ... but still no wifi connection

---

### Post by chili555 on 2013-08-23
Please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
```Now download this package to your desktop: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1-snpc.tar.bz2)

Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/compat-wireless-3.6.6-1-snpc
./scripts/driver-select ath
make
sudo make install
sudo modprobe ath9k
```Now is the wireless working?

---

### Post by tahir2 on 2013-08-23
now its stuck here 

sudo modprobe ath9k
WARNING: Error inserting ath9k_hw (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Invalid argument
WARNING: Error inserting ath9k_common (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Invalid argument
WARNING: Error inserting mac80211 (/lib/modules/3.5.0-23-generic/updates/net/mac80211/mac80211.ko): Invalid argument
FATAL: Error inserting ath9k (/lib/modules/3.5.0-23-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument

---

### Post by chili555 on 2013-08-23
Close the process with Ctrl+c. Please try a reboot.

---

### Post by tahir2 on 2013-08-23
same result .. after restarting tried all your instruction again .. but same result in last command

---

### Post by chili555 on 2013-08-23
If you do nothing, did ath9k load on boot without you needing to load it explicitly?```
lsmod | grep ath
```Were there errors or warnings at 'make' or 'sudo make install?' What does this tell us?```
dmesg | grep ath
```

---

### Post by tahir2 on 2013-08-23
no it didn't boot by itslef nothing happened before unplugged my ethernet so to reboot normally and give wifi time if it's working ...  and no mae and sudo make install went smoothly no errors. and here's the result of ur command 

dmesg | grep ath

[   18.754290] type=1400 audit(1377302433.321:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=931 comm="apparmor_parser"
[  240.697369] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
[  240.697373] ath: Unknown symbol wiphy_apply_custom_regulatory (err -22)
[  240.697393] ath: disagrees about version of symbol freq_reg_info
[  240.697396] ath: Unknown symbol freq_reg_info (err -22)
[ 1034.964997] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
[ 1034.965005] ath: Unknown symbol wiphy_apply_custom_regulatory (err -22)
[ 1034.965030] ath: disagrees about version of symbol freq_reg_info
[ 1034.965033] ath: Unknown symbol freq_reg_info (err -22)

---

### Post by chili555 on 2013-08-23
Just a few minutes. I am going to start up a live CD for 12.04 and compile it myself and troubleshoot. Be back soon.

Ref:  [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/07/12/](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/07/12/)

---

### Post by tahir2 on 2013-08-23
ok no problem .. i'll be waiting

---

### Post by chili555 on 2013-08-23
Please do:```
cd Desktop/compat-wireless-3.6.6-1-snpc
sudo make uninstall
```Reboot. Download this package to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/2013/07/12/backports-20130712.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/2013/07/12/backports-20130712.tar.bz2)

Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/backports-20130712
make defconfig-ath9k
make
sudo make install
```Reboot and post:```
dmesg | grep ath
iwconfig
```

---

### Post by tahir2 on 2013-08-23
yep .. thanks alot its working now ...

---

### Post by tahir2 on 2013-08-23
here's the command results 

dmesg | grep ath
[   18.643689] ath: phy0: ASPM enabled: 0x43
[   18.643691] ath: EEPROM regdomain: 0x6a
[   18.643692] ath: EEPROM indicates we should expect a direct regpair map
[   18.643695] ath: Country alpha2 being used: 00
[   18.643695] ath: Regpair used: 0x6a
[   18.849733] Registered led device: ath9k-phy0
[   18.915555] type=1400 audit(1377310282.481:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=962 comm="apparmor_parser"
[   71.215510] ath: regdomain 0x809e updated by CountryIE
[   71.215512] ath: EEPROM regdomain: 0x809e
[   71.215513] ath: EEPROM indicates we should expect a country code
[   71.215514] ath: doing EEPROM country->regdmn map search
[   71.215515] ath: country maps to regdmn code: 0x50
[   71.215516] ath: Country alpha2 being used: TW
[   71.215517] ath: Regpair used: 0x50
[   78.659879] ath: regdomain 0x809e updated by CountryIE
[   78.659882] ath: EEPROM regdomain: 0x809e
[   78.659884] ath: EEPROM indicates we should expect a country code
[   78.659885] ath: doing EEPROM country->regdmn map search
[   78.659886] ath: country maps to regdmn code: 0x50
[   78.659887] ath: Country alpha2 being used: TW
[   78.659888] ath: Regpair used: 0x50
[   83.979325] ath: regdomain 0x809e updated by CountryIE
[   83.979329] ath: EEPROM regdomain: 0x809e
[   83.979330] ath: EEPROM indicates we should expect a country code
[   83.979332] ath: doing EEPROM country->regdmn map search
[   83.979333] ath: country maps to regdmn code: 0x50
[   83.979335] ath: Country alpha2 being used: TW
[   83.979336] ath: Regpair used: 0x50
[   89.383531] ath: regdomain 0x809e updated by CountryIE
[   89.383533] ath: EEPROM regdomain: 0x809e
[   89.383534] ath: EEPROM indicates we should expect a country code
[   89.383535] ath: doing EEPROM country->regdmn map search
[   89.383536] ath: country maps to regdmn code: 0x50
[   89.383537] ath: Country alpha2 being used: TW
[   89.383538] ath: Regpair used: 0x50
[   92.308273] ath: regdomain 0x809e updated by CountryIE
[   92.308275] ath: EEPROM regdomain: 0x809e
[   92.308276] ath: EEPROM indicates we should expect a country code
[   92.308277] ath: doing EEPROM country->regdmn map search
[   92.308278] ath: country maps to regdmn code: 0x50
[   92.308279] ath: Country alpha2 being used: TW
[   92.308280] ath: Regpair used: 0x50
[   99.522056] ath: regdomain 0x809e updated by CountryIE
[   99.522059] ath: EEPROM regdomain: 0x809e
[   99.522059] ath: EEPROM indicates we should expect a country code
[   99.522061] ath: doing EEPROM country->regdmn map search
[   99.522061] ath: country maps to regdmn code: 0x50
[   99.522062] ath: Country alpha2 being used: TW
[   99.522063] ath: Regpair used: 0x50
[  106.911573] ath: regdomain 0x809e updated by CountryIE
[  106.911578] ath: EEPROM regdomain: 0x809e
[  106.911580] ath: EEPROM indicates we should expect a country code
[  106.911583] ath: doing EEPROM country->regdmn map search
[  106.911585] ath: country maps to regdmn code: 0x50
[  106.911587] ath: Country alpha2 being used: TW
[  106.911589] ath: Regpair used: 0x50
[  120.656560] ath: regdomain 0x809e updated by CountryIE
[  120.656562] ath: EEPROM regdomain: 0x809e
[  120.656563] ath: EEPROM indicates we should expect a country code
[  120.656564] ath: doing EEPROM country->regdmn map search
[  120.656565] ath: country maps to regdmn code: 0x50
[  120.656566] ath: Country alpha2 being used: TW
[  120.656567] ath: Regpair used: 0x50
[  127.960607] ath: regdomain 0x809e updated by CountryIE
[  127.960609] ath: EEPROM regdomain: 0x809e
[  127.960610] ath: EEPROM indicates we should expect a country code
[  127.960611] ath: doing EEPROM country->regdmn map search
[  127.960612] ath: country maps to regdmn code: 0x50
[  127.960613] ath: Country alpha2 being used: TW
[  127.960614] ath: Regpair used: 0x50
[  135.229414] ath: regdomain 0x809e updated by CountryIE
[  135.229416] ath: EEPROM regdomain: 0x809e
[  135.229417] ath: EEPROM indicates we should expect a country code
[  135.229418] ath: doing EEPROM country->regdmn map search
[  135.229419] ath: country maps to regdmn code: 0x50
[  135.229420] ath: Country alpha2 being used: TW
[  135.229421] ath: Regpair used: 0x50
[  142.483772] ath: regdomain 0x809e updated by CountryIE
[  142.483774] ath: EEPROM regdomain: 0x809e
[  142.483775] ath: EEPROM indicates we should expect a country code
[  142.483776] ath: doing EEPROM country->regdmn map search
[  142.483777] ath: country maps to regdmn code: 0x50
[  142.483778] ath: Country alpha2 being used: TW
[  142.483779] ath: Regpair used: 0x50
[  149.748524] ath: regdomain 0x809e updated by CountryIE
[  149.748529] ath: EEPROM regdomain: 0x809e
[  149.748531] ath: EEPROM indicates we should expect a country code
[  149.748534] ath: doing EEPROM country->regdmn map search
[  149.748536] ath: country maps to regdmn code: 0x50
[  149.748538] ath: Country alpha2 being used: TW
[  149.748540] ath: Regpair used: 0x50
[  156.913782] ath: regdomain 0x809e updated by CountryIE
[  156.913785] ath: EEPROM regdomain: 0x809e
[  156.913786] ath: EEPROM indicates we should expect a country code
[  156.913787] ath: doing EEPROM country->regdmn map search
[  156.913789] ath: country maps to regdmn code: 0x50
[  156.913790] ath: Country alpha2 being used: TW
[  156.913791] ath: Regpair used: 0x50
[  164.076031] ath: regdomain 0x809e updated by CountryIE
[  164.076036] ath: EEPROM regdomain: 0x809e
[  164.076038] ath: EEPROM indicates we should expect a country code
[  164.076041] ath: doing EEPROM country->regdmn map search
[  164.076043] ath: country maps to regdmn code: 0x50
[  164.076045] ath: Country alpha2 being used: TW
[  164.076047] ath: Regpair used: 0x50
[  171.440325] ath: regdomain 0x809e updated by CountryIE
[  171.440330] ath: EEPROM regdomain: 0x809e
[  171.440332] ath: EEPROM indicates we should expect a country code
[  171.440335] ath: doing EEPROM country->regdmn map search
[  171.440337] ath: country maps to regdmn code: 0x50
[  171.440339] ath: Country alpha2 being used: TW
[  171.440341] ath: Regpair used: 0x50
[  178.692991] ath: regdomain 0x809e updated by CountryIE
[  178.692994] ath: EEPROM regdomain: 0x809e
[  178.692995] ath: EEPROM indicates we should expect a country code
[  178.692996] ath: doing EEPROM country->regdmn map search
[  178.692998] ath: country maps to regdmn code: 0x50
[  178.692999] ath: Country alpha2 being used: TW
[  178.693000] ath: Regpair used: 0x50
[  271.610683] ath: regdomain 0x809e updated by CountryIE
[  271.610686] ath: EEPROM regdomain: 0x809e
[  271.610687] ath: EEPROM indicates we should expect a country code
[  271.610689] ath: doing EEPROM country->regdmn map search
[  271.610690] ath: country maps to regdmn code: 0x50
[  271.610691] ath: Country alpha2 being used: TW
[  271.610692] ath: Regpair used: 0x50

iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NetComm Wireless 4021"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:60:64:73:8A:EE   
          Bit Rate=120 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:50   Missed beacon:0

---

### Post by chili555 on 2013-08-24
Looks just great! The driver you compiled is for your current kernel version only. When a newer kernel is installed by Update Manager, you will need to recompile:```
cd Desktop/backports-20130712
make clean
make defconfig-ath9k
make
sudo make install
sudo modprobe ath9k
```Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

