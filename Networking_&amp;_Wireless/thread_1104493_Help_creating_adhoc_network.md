---
title: "Help creating adhoc network"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by ace214 on 2009-03-23
Problem: My university uses WPA2 networks but my Nintendo DS can only connect to WEP or unsecured networks. I'm looking for a way to create some kind of adhoc network or something so that I can use the wireless on my DS at school.

I need to use my laptop for this and it would be ideal if there was some way to use my wireless to connect to the adhoc and to my school's wireless at the same time, but I don't think this is possible. (The reason I want to do this is because I can't seem to get an IP address from the ethernet in my office with Ubuntu.)

When I try to make an adhoc network with Network Manager I get this output:
```
ar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) starting connection 'testadhoc' 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'testadhoc' requires no security.  No secrets needed. 
Mar 23 18:18:46 laptop NetworkManager: <info>  Config: added 'ssid' value 'testadhoc' 
Mar 23 18:18:46 laptop avahi-daemon[3216]: Withdrawing address record for 170.140.106.45 on eth1.
Mar 23 18:18:46 laptop avahi-daemon[3216]: Leaving mDNS multicast group on interface eth1.IPv4 with address 170.140.106.45.
Mar 23 18:18:46 laptop avahi-daemon[3216]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 18:18:46 laptop dnsmasq[4838]: no servers found in /etc/resolv.conf, will retry
Mar 23 18:18:46 laptop NetworkManager: <info>  Config: added 'mode' value '1' 
Mar 23 18:18:46 laptop NetworkManager: <info>  Config: added 'frequency' value '2412' 
Mar 23 18:18:46 laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): supplicant connection state:  completed -> disconnected 
Mar 23 18:18:46 laptop NetworkManager: <info>  Config: set interface ap_scan to 2 
Mar 23 18:18:46 laptop kernel: [  457.421968] ipw2200 0000:06:04.0: firmware: requesting ipw2200-ibss.fw
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): supplicant connection state:  associated -> completed 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'testadhoc'. 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Mar 23 18:18:46 laptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Mar 23 18:18:46 laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Mar 23 18:18:46 laptop avahi-daemon[3216]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.42.43.1.
Mar 23 18:18:46 laptop avahi-daemon[3216]: New relevant interface eth1.IPv4 for mDNS.
Mar 23 18:18:46 laptop avahi-daemon[3216]: Registering new address record for 10.42.43.1 on eth1.IPv4.
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol tcp --destination-port 53 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol udp --destination-port 53 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol tcp --destination-port 67 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol udp --destination-port 67 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth1 --jump REJECT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth1 --jump REJECT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth1 --out-interface eth1 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth1 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth1 --match state --state ESTABLISHED,RELATED --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE 
Mar 23 18:18:47 laptop NetworkManager: <info>  Starting dnsmasq... 
Mar 23 18:18:47 laptop NetworkManager: <debug> [1237846727.733234] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --no-poll --except-interface=lo --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth1.pid 
[B]Mar 23 18:18:47 laptop dnsmasq[5264]: failed to bind listening socket for 10.42.43.1: Address already in use
Mar 23 18:18:47 laptop dnsmasq[5264]: FAILED to start up[/B]
Mar 23 18:18:47 laptop NetworkManager: <debug> [1237846727.743101] nm_dnsmasq_manager_start(): dnsmasq started with pid 5264 
Mar 23 18:18:47 laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Mar 23 18:18:47 laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Mar 23 18:18:47 laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 23 18:18:47 laptop NetworkManager: dnsmasq exited with error: Network access problem (address in use; permissions; etc) (2)
Mar 23 18:18:47 laptop NetworkManager: <info>  (eth1): device state change: 8 -> 9 
Mar 23 18:18:47 laptop NetworkManager: <info>  Activation (eth1) failed for access point (testadhoc) 
Mar 23 18:18:47 laptop NetworkManager: <info>  Marking connection 'testadhoc' invalid. 
Mar 23 18:18:47 laptop NetworkManager: <info>  Activation (eth1) failed. 
Mar 23 18:18:47 laptop NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Mar 23 18:18:47 laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE 
Mar 23 18:18:47 laptop avahi-daemon[3216]: Withdrawing address record for 10.42.43.1 on eth1.
Mar 23 18:18:47 laptop avahi-daemon[3216]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.42.43.1.
Mar 23 18:18:47 laptop avahi-daemon[3216]: Interface eth1.IPv4 no longer relevant for mDNS.
Mar 23 18:18:47 laptop kernel: [  459.027119] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth1 --match state --state ESTABLISHED,RELATED --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth1 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth1 --out-interface eth1 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --out-interface eth1 --jump REJECT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface eth1 --jump REJECT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth1 --protocol udp --destination-port 67 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth1 --protocol tcp --destination-port 67 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth1 --protocol udp --destination-port 53 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface eth1 --protocol tcp --destination-port 53 --jump ACCEPT 
Mar 23 18:18:47 laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto EmoryUnplugged' 
```

But for short, I think the relevant piece is ```
Mar 23 18:18:47 laptop dnsmasq[5264]: failed to bind listening socket for 10.42.43.1: Address already in use
Mar 23 18:18:47 laptop dnsmasq[5264]: FAILED to start up
```

Can't figure out how to fix this...

Thanks for any help with this specific error and advice to solve the general problem...

---

### Post by ace214 on 2009-03-27
bump

---

### Post by dav2dev on 2009-04-22
Hi, i had this problem and it seems that dsnmasq was already active when i tryed to activate adhoc network. So the solution was:
sudo pkill dnsmasq
then try to create adhoc network again.
Let me know if this works for you :)

---

