---
title: "Share wireless network connection with wired Ethernet"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by lpc921 on 2012-02-09
I'm using Ubuntu 11.10. I have 2 network adaptors on my computer. One wired and one wireless. They both work fine on their own. Now I want to provide Internet through cable to another device which does not have a wireless adaptor.

If I enable the wired connection (not on Internet) with the wireless connection (on Internet) then I can't connect to Internet at all.

I would like to setup a static IP for my wired Ethernet connection and use it as a gateway, and also a static IP on the other device. In the network manager, I've changed the ipv4 setting to "Shared to other computers" for the wired connection only/for the wireless connection only/for both wired and wireless connection, but non of them worked.

---

### Post by lpc921 on 2012-02-10
I've set ipv6 setting to ignore and removed dnsmasq. Here is the log of NetworkManager
```
Feb 11 15:27:53 user NetworkManager[960]: <info> (eth0): carrier now OFF (device state 30)
Feb 11 15:27:53 user NetworkManager[960]: <info> (eth0): device state change: disconnected -> unavailable (reason 'carrier-changed') [30 20 40]
Feb 11 15:27:53 user NetworkManager[960]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Feb 11 15:27:53 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:27:53 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:27:56 user NetworkManager[960]: <info> (eth0): carrier now ON (device state 20)
Feb 11 15:27:56 user NetworkManager[960]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Feb 11 15:27:56 user NetworkManager[960]: <info> Auto-activating connection 'Wired connection 1'.
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) starting connection 'Wired connection 1'
Feb 11 15:27:56 user NetworkManager[960]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 11 15:27:56 user NetworkManager[960]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 11 15:27:56 user NetworkManager[960]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 11 15:27:56 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 11 15:27:57 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:27:57 user NetworkManager[960]: <error> [1328927277.701258] [nm-device.c:2577] start_sharing(): (eth0/eth0): failed to start dnsmasq: Could not find dnsmasq binary.
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:27:57 user NetworkManager[960]: <warn> Activation (eth0) Stage 5 of 5 (IP Configure Commit) start sharing failed.
Feb 11 15:27:57 user NetworkManager[960]: <info> (eth0): device state change: ip-config -> failed (reason 'sharing-start-failed') [70 120 18]
Feb 11 15:27:57 user NetworkManager[960]: <warn> Activation (eth0) failed.
Feb 11 15:27:57 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 11 15:27:57 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 11 15:27:57 user NetworkManager[960]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 11 15:27:57 user NetworkManager[960]: <info> (eth0): deactivating device (reason 'none') [0]
Feb 11 15:27:57 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:27:57 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:00 user NetworkManager[960]: <info> Auto-activating connection 'Wired connection 1'.
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) starting connection 'Wired connection 1'
Feb 11 15:28:00 user NetworkManager[960]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 11 15:28:00 user NetworkManager[960]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 11 15:28:00 user NetworkManager[960]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 11 15:28:00 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 11 15:28:01 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:28:01 user NetworkManager[960]: <error> [1328927281.993610] [nm-device.c:2577] start_sharing(): (eth0/eth0): failed to start dnsmasq: Could not find dnsmasq binary.
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:28:01 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:28:02 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:28:02 user NetworkManager[960]: <warn> Activation (eth0) Stage 5 of 5 (IP Configure Commit) start sharing failed.
Feb 11 15:28:02 user NetworkManager[960]: <info> (eth0): device state change: ip-config -> failed (reason 'sharing-start-failed') [70 120 18]
Feb 11 15:28:02 user NetworkManager[960]: <warn> Activation (eth0) failed.
Feb 11 15:28:02 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 11 15:28:02 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 11 15:28:02 user NetworkManager[960]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 11 15:28:02 user NetworkManager[960]: <info> (eth0): deactivating device (reason 'none') [0]
Feb 11 15:28:02 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:02 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:04 user NetworkManager[960]: <info> Auto-activating connection 'Wired connection 1'.
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) starting connection 'Wired connection 1'
Feb 11 15:28:04 user NetworkManager[960]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 11 15:28:04 user NetworkManager[960]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 11 15:28:04 user NetworkManager[960]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 11 15:28:04 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 11 15:28:05 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:28:05 user NetworkManager[960]: <error> [1328927285.993436] [nm-device.c:2577] start_sharing(): (eth0/eth0): failed to start dnsmasq: Could not find dnsmasq binary.
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:28:05 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:28:06 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:28:06 user NetworkManager[960]: <warn> Activation (eth0) Stage 5 of 5 (IP Configure Commit) start sharing failed.
Feb 11 15:28:06 user NetworkManager[960]: <info> (eth0): device state change: ip-config -> failed (reason 'sharing-start-failed') [70 120 18]
Feb 11 15:28:06 user NetworkManager[960]: <warn> Activation (eth0) failed.
Feb 11 15:28:06 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 11 15:28:06 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 11 15:28:06 user NetworkManager[960]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 11 15:28:06 user NetworkManager[960]: <info> (eth0): deactivating device (reason 'none') [0]
Feb 11 15:28:06 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:06 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:08 user NetworkManager[960]: <info> Auto-activating connection 'Wired connection 1'.
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) starting connection 'Wired connection 1'
Feb 11 15:28:08 user NetworkManager[960]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb 11 15:28:08 user NetworkManager[960]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Feb 11 15:28:08 user NetworkManager[960]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 11 15:28:08 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Feb 11 15:28:09 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:28:09 user NetworkManager[960]: <error> [1328927289.995486] [nm-device.c:2577] start_sharing(): (eth0/eth0): failed to start dnsmasq: Could not find dnsmasq binary.
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 11 15:28:09 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth0 --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --out-interface eth0 --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth0 --jump REJECT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth0 --jump REJECT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 11 15:28:10 user NetworkManager[960]: <warn> Activation (eth0) Stage 5 of 5 (IP Configure Commit) start sharing failed.
Feb 11 15:28:10 user NetworkManager[960]: <info> (eth0): device state change: ip-config -> failed (reason 'sharing-start-failed') [70 120 18]
Feb 11 15:28:10 user NetworkManager[960]: <info> Marking connection 'Wired connection 1' invalid.
Feb 11 15:28:10 user NetworkManager[960]: <warn> Activation (eth0) failed.
Feb 11 15:28:10 user NetworkManager[960]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 11 15:28:10 user NetworkManager[960]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 11 15:28:10 user NetworkManager[960]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 11 15:28:10 user NetworkManager[960]: <info> (eth0): deactivating device (reason 'none') [0]
Feb 11 15:28:10 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
Feb 11 15:28:10 user NetworkManager[960]: <info> Policy set 'UoA-WiFi' (wlan0) as default for IPv4 routing and DNS.
```Edit: It's solved after installing dnsmasq-base from the repo.

---

