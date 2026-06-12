---
title: "usb modem disconnected after 1 second"
date: 2012-01-31
forum: Networking &amp; Wireless
---

### Post by weiliang on 2012-01-31
Hi,
As the title said, my usb modem always disconnected after 1 second connected.
I found out that if my eth0 cable is plugged then ppp0 is not disconnected, otherwise if I unplugged my eth0 cable then connect the modem, the ppp0 always disconnected.
I suspect that I have misconfigured my ubuntu Natty, but I have no clue of that. I hope someone here could guide me how to fix this. Thanks

syslog> Jan 31 15:23:39 william pppd[14943]: Using interface ppp0
Jan 31 15:23:39 william pppd[14943]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 31 15:23:39 william pppd[14943]: CHAP authentication succeeded
Jan 31 15:23:39 william pppd[14943]: CHAP authentication succeeded
Jan 31 15:23:42 william pppd[14943]: Could not determine remote IP address: defaulting to 10.64.64.64 **--> This is also a weird message**
Jan 31 15:23:42 william pppd[14943]: local  IP address 10.214.132.53
Jan 31 15:23:42 william pppd[14943]: remote IP address 10.64.64.64
Jan 31 15:23:42 william pppd[14943]: primary   DNS address 112.215.71.243
Jan 31 15:23:42 william pppd[14943]: secondary DNS address 112.215.71.242
Jan 31 15:23:42 william NetworkManager[611]: <info> PPP manager(IP Config Get) reply received.
Jan 31 15:23:42 william NetworkManager[611]: <info> Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 31 15:23:42 william NetworkManager[611]: <info> Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 31 15:23:42 william NetworkManager[611]: <info> Scheduling stage 5
Jan 31 15:23:42 william NetworkManager[611]: <info> Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 31 15:23:42 william NetworkManager[611]: <info> Done scheduling stage 5
Jan 31 15:23:42 william NetworkManager[611]: <info> Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 31 15:23:42 william NetworkManager[611]: <info> Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started...
Jan 31 15:23:43 william NetworkManager[611]: <info> Policy set 'eth0' (eth0) as default for IPv4 routing and DNS.
Jan 31 15:23:43 william NetworkManager[611]: <info> (ttyUSB0): device state change: 7 -> 8 (reason 0)
Jan 31 15:23:43 william NetworkManager[611]: <info> Activation (ttyUSB0) successful, device activated.
Jan 31 15:23:43 william NetworkManager[611]: <info> Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 31 15:23:53 william ntpdate[15001]: no server suitable for synchronization found
Jan 31 15:25:31 william NetworkManager[611]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds) **--> eth0 unplugged after ppp0 connected**
Jan 31 15:25:31 william kernel: [26153.652213] r8169 0000:06:00.0: eth0: link down
Jan 31 15:25:36 william NetworkManager[611]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Jan 31 15:25:36 william NetworkManager[611]: <info> (eth0): deactivating device (reason: 40).
Jan 31 15:25:36 william avahi-daemon[613]: Withdrawing address record for 192.168.128.247 on eth0.
Jan 31 15:25:36 william avahi-daemon[613]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.128.247.
Jan 31 15:25:36 william avahi-daemon[613]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 31 15:25:36 william NetworkManager[611]: <info> Policy set 'XL Unlimited' (ppp0) as default for IPv4 routing and DNS.
Jan 31 15:25:36 william NetworkManager[611]: <info> Policy set 'XL Unlimited' (ppp0) as default for IPv4 routing and DNS.
Jan 31 15:25:40 william pppd[14943]: LCP terminated by peer **--> suddenly ppp0 is disconnected too**
Jan 31 15:25:40 william pppd[14943]: Connect time 2.0 minutes.
Jan 31 15:25:40 william pppd[14943]: Sent 850 bytes, received 0 bytes.
Jan 31 15:25:40 william pppd[14943]: Modem hangup
Jan 31 15:25:40 william pppd[14943]: Connection terminated.
Jan 31 15:25:40 william NetworkManager[611]: <info> (ttyUSB0): device state change: 8 -> 9 (reason 13)
Jan 31 15:25:40 william NetworkManager[611]: <warn> Activation (ttyUSB0) failed.
Jan 31 15:25:40 william NetworkManager[611]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jan 31 15:25:40 william NetworkManager[611]: <info> (ttyUSB0): deactivating device (reason: 0).
Jan 31 15:25:40 william modem-manager[617]: <info>  (ttyUSB0) closing serial port...
Jan 31 15:25:40 william modem-manager[617]: <info>  (ttyUSB0) serial port closed
Jan 31 15:25:40 william modem-manager[617]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Jan 31 15:25:40 william modem-manager[617]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> connected)
Jan 31 15:25:40 william avahi-daemon[613]: Withdrawing workstation service for ppp0.
Jan 31 15:25:40 william NetworkManager[611]: <warn> could not read ppp stats: No such device
Jan 31 15:25:40 william pppd[14943]: Exit.
Jan 31 15:25:40 william NetworkManager[611]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 31 15:25:40 william NetworkManager[611]: <info> disconnect failed: (32) The serial port is not open.

---

### Post by weiliang on 2012-02-01
No one could help me?

---

