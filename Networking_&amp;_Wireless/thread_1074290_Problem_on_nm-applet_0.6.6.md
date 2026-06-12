---
title: "Problem on nm-applet 0.6.6"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by BrillianceLin on 2009-02-19
Hi, I just manage to install 804lts. It works very well at the beginning, but after I update the system. It seems like there is problem on nm-applet network manager program. I will lost my connection once a while. But the network manager will not tell me any thing. Until I try to open a website, and it fail. Then I look at the system monitor. The router stop talking to my computer. So, I have to manually force the network manager reconnect to the router. It was not like this on my 710 and before I run the live usb.

Any idea? 

When this thing happen the system log has this
message
Feb 19 02:59:11 laptop kernel: [12700.973456] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu

syslog
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Feb 19 02:59:17 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers

Did not see anything unusual in other log...(maybe)

---

### Post by BrillianceLin on 2009-02-19
I hope the system log will give some clue~~

---

### Post by BrillianceLin on 2009-02-19
these message were found on kernel log
Feb 19 04:12:23  kernel: [17090.147311] iwl3945: Microcode SW error detected.  Restarting 0x2000008.
Feb 19 04:12:24  kernel: [17091.141061] iwl3945: Can't stop Rx DMA.

so? Is it the driver no good? kernel no good? or net work manger no good?

---

