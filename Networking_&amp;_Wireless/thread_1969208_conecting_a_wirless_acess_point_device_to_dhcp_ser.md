---
title: "conecting a wirless acess point device to dhcp server"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by flox12 on 2012-04-29
hello everyone.
am a new bee to ubuntu been using it for a few month now. i was able to install a dhcp server but some how i was not able to make it run with my access point so i can share INTERNET and to other user in my small home network. 
any help will be thankful
syslog
> 
 Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) started...
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Marking connection 'Wired connection 1' invalid.
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <warn> Activation (eth0) failed.
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> (eth0): deactivating device (reason 'none') [0]
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> (eth0): canceled DHCP transaction, DHCP client pid 17247
Apr 30 03:20:15 flox-HP-Compaq-dc5700-Microtower NetworkManager[931]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
flox@flox-HP-Compaq-dc5700-Microtower:~$ sudo /etc/init.d/isc-dhcp-server start
 * Starting ISC DHCP server dhcpd                                                                                                                               * check syslog for diagnostics.
                                                                                                                                                        [fail]  

---

