---
title: "No network after suspend to ram"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by tulskiy on 2010-02-07
I know there are hundreds of similar questions about suspend on Ubuntu, but none of the fixes they use work for me.

This bug is the only thing that stops me from using Ubuntu - I put computer to sleep (suspend to ram) and after resume I have no network. The only  way to get network back is to restart.

Looking at the logs, it seems that NetworkManager starts, finds the device and then fails to complete DHCP transaction.

I don't know what causes the problem, probably this line: "via-rhine: Reset not complete yet. Trying harder."

Does anyone know possible reason for this?

Here is the log:

> Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Feb  7 14:30:21 tulskiy-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Feb  7 14:30:21 tulskiy-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  7 14:30:21 tulskiy-desktop dhclient: All rights reserved.
Feb  7 14:30:21 tulskiy-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Feb  7 14:30:21 tulskiy-desktop dhclient: 
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  dhclient started with pid 4081
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Beginning IP6 addrconf.
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb  7 14:30:21 tulskiy-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Feb  7 14:30:21 tulskiy-desktop dhclient: Listening on LPF/eth0/00:19:66:89:76:a4
Feb  7 14:30:21 tulskiy-desktop dhclient: Sending on   LPF/eth0/00:19:66:89:76:a4
Feb  7 14:30:21 tulskiy-desktop dhclient: Sending on   Socket/fallback
Feb  7 14:30:24 tulskiy-desktop dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Feb  7 14:30:28 tulskiy-desktop dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Feb  7 14:30:32 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb  7 14:30:32 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Feb  7 14:30:32 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb  7 14:30:35 tulskiy-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb  7 14:30:42 tulskiy-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb  7 14:30:44 tulskiy-desktop kernel: [15488.004974] eth0: Transmit timed out, status ffff, PHY status ffff, resetting...
Feb  7 14:30:44 tulskiy-desktop kernel: [15488.005040] via-rhine: Reset not complete yet. Trying harder.
Feb  7 14:30:44 tulskiy-desktop kernel: [15488.009873] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Feb  7 14:30:55 tulskiy-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 4081
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  Activation (eth0) failed.
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Feb  7 14:31:07 tulskiy-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0).

---

### Post by tulskiy on 2010-02-08
OK, I found a workaround: unloading and loading via-rhine with modprobe fixes the network.

Now the question - I know that there should be some script or config file where I should just say to reload via-rhine after suspend. Where is it located in Karmic? Most of the config files mentioned on other forums do not exist on my system.

---

### Post by tulskiy on 2010-02-08
Just to finish my monologue, solution is [here]("http://ubuntuforums.org/showthread.php?t=1061810")

I just had to create file 90reload_network in /etc/pm/config.d with this code:
 ```
SUSPEND_MODULES="$SUSPEND_MODULES via-rhine"
```

---

### Post by Spirit of Yggdrasill on 2010-06-10
Thanks works like a charm :-)
My laptop is MSI vr610x.

---

