---
title: "Karmic mobile internet dowsnt work"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by janrikard on 2009-12-03
after upgrade to karmic my mobile internet doesnt work. it connects and reports working, but i cant connect to anything it worked fine before upgrade

lsusb gives this modem
Bus 001 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

and the syslog reports this

Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) starting connection '3 Bredband 1'
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Dec  3 22:02:29 rikard-eee modem-manager: (ttyUSB0) opening serial device...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Starting pppd connection
Dec  3 22:02:29 rikard-eee NetworkManager: <debug> [1259874149.483486] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Dec  3 22:02:29 rikard-eee NetworkManager: <debug> [1259874149.511436] nm_ppp_manager_start(): ppp started with pid 3872
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
Dec  3 22:02:29 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
Dec  3 22:02:29 rikard-eee pppd[3872]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec  3 22:02:29 rikard-eee pppd[3872]: pppd 2.4.5 started by root, uid 0
Dec  3 22:02:29 rikard-eee pppd[3872]: Using interface ppp0
Dec  3 22:02:29 rikard-eee NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec  3 22:02:29 rikard-eee NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec  3 22:02:29 rikard-eee pppd[3872]: Connect: ppp0 <--> /dev/ttyUSB0
Dec  3 22:02:29 rikard-eee pppd[3872]: CHAP authentication succeeded
Dec  3 22:02:29 rikard-eee pppd[3872]: CHAP authentication succeeded
Dec  3 22:02:37 rikard-eee pppd[3872]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec  3 22:02:37 rikard-eee pppd[3872]: Cannot determine ethernet address for proxy ARP
Dec  3 22:02:37 rikard-eee pppd[3872]: local  IP address 95.209.11.164
Dec  3 22:02:37 rikard-eee pppd[3872]: remote IP address 10.64.64.64
Dec  3 22:02:37 rikard-eee NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Dec  3 22:02:37 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec  3 22:02:37 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) started...
Dec  3 22:02:37 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled...
Dec  3 22:02:37 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec  3 22:02:37 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started...
Dec  3 22:02:38 rikard-eee NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 (reason 0)
Dec  3 22:02:38 rikard-eee NetworkManager: <info>  Policy set '3 Bredband 1' (ppp0) as default for routing and DNS.
Dec  3 22:02:38 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) successful, device activated.
Dec  3 22:02:38 rikard-eee NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.
Dec  3 22:02:38 rikard-eee nm-dispatcher.action: Tried to set deprecated property gsm/band
Dec  3 22:02:38 rikard-eee NetworkManager: Tried to set deprecated property gsm/band
Dec  3 22:02:38 rikard-eee NetworkManager: Tried to set deprecated property gsm/band
Dec  3 22:02:38 rikard-eee ntpdate[3934]: can't find host ntp.ubuntu.com
Dec  3 22:02:38 rikard-eee ntpdate[3934]: no servers can be used, exiting
Dec  3 22:02:43 rikard-eee NetworkManager: Tried to set deprecated property gsm/band
Dec  3 22:02:43 rikard-eee NetworkManager: Tried to set deprecated property gsm/band

anyone have any idea whats wrong?

/rikard

---

### Post by fromans on 2009-12-16
I have the exact same problem. Usually I just have to disconnect/reconnect the modem and repeatedly try to connect to AT&T until it works. I'm using the AT&T Mercury USB modem. I wish someone could pin this down. I've seen bug reports that are similar but no solution yet.

---

### Post by alexfish on 2009-12-16
Hi

can I ask Your Location

Thanks in Advance

alexfish

If its uk  also look at screen shot


**[B][FONT=Verdana, Arial][COLOR=#000080][3]("http://www.filesaveas.com/redirect.php?id=three&ref=FSAgprs") GPRS Data settings:[/COLOR][/FONT]**[/B]

         **[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]Homepage: [/COLOR][/SIZE][/FONT]**[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]http://mobile.three.co.uk/[/COLOR][/SIZE][/FONT][B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]
      Access Point (contract): [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]three.co.uk[/COLOR][/SIZE][/FONT]
      **[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]           Username : [/COLOR][/SIZE][/FONT]**[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]guest[/COLOR][/SIZE][/FONT][B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]
            Password: [/COLOR][/SIZE][/FONT][/B][FONT=Verdana, Arial][SIZE=2][COLOR=#000080]guest[/COLOR][/SIZE][/FONT]
[FONT=Verdana, Arial][SIZE=2][COLOR=#000080]**Authentication: **Normal[/COLOR][/SIZE][/FONT]

---

