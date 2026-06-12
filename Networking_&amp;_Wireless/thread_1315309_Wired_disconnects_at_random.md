---
title: "Wired disconnects at random"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by David904 on 2009-11-05
Hey everyone,

This is the second time I am using Ubuntu (9.10) on my Dell C521 with a broadcom 440x ethernet card. My internet is plugged in to my computer directly, never had troubles with my internet with other OSs. My problem is that when I use internet, especially when downloading, my internet disconnects at random. Needles to say this is very annoying and makes it hard to work.

Can you guys help me out? I don't know very much about computers or ubuntu in general, but followed the troubleshooting page on the ubuntu site, which didn't show any troubles with my internet.

Thanks in advance,

David

---

### Post by Earl-Grey on 2009-11-05
Sorry I don't think I can help you, but I know some ISP's are not happy with people using Bittorrent and other download programs. Could they be blocking you from using Bittorrent, if that is what you use to download?

I am not sure what it is, but there is a command line for linux that allows you to check the name of your Network Adapter. Maybe it using the wrong driver?

---

### Post by pendelton on 2009-11-05
I have a similar problem. I have a HP laptop with 9.10 that I am unable to get the wireless working on so have to use a cable connection for networking. However, after an hour or so the network disconnects and won't reconnect. Currently I have to reboot to get it working again.

Other 9.4 Ubuntu machine on the same network work fine. I've even swapped machines over to test the connection points but the 9.10 machine always disconnects on its own at some point regardless.

I also have windows on the 9.10 machine and the network is fine so I'm sure that the network card is fine. Any ideas anyone?

---

### Post by shredder12 on 2009-11-06
could you post the output of network manager logs(last 50-100 lines) /var/log/daemon.log when your network disconnects..
I could point out a bit to what is really happening.

---

### Post by David904 on 2009-11-06
```
Nov  6 16:52:36 david-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Nov  6 16:52:36 david-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Nov  6 16:52:36 david-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40). 
Nov  6 16:52:36 david-desktop NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 4444 
Nov  6 16:52:36 david-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Nov  6 16:52:36 david-desktop avahi-daemon[2830]: Withdrawing address record for 82.139.118.3 on eth0.
Nov  6 16:52:36 david-desktop avahi-daemon[2830]: Leaving mDNS multicast group on interface eth0.IPv4 with address 82.139.118.3.
Nov  6 16:52:36 david-desktop avahi-daemon[2830]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov  6 16:52:39 david-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  dhclient started with pid 5163 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  6 16:52:39 david-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  6 16:52:39 david-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  6 16:52:39 david-desktop dhclient: All rights reserved.
Nov  6 16:52:39 david-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  6 16:52:39 david-desktop dhclient: 
Nov  6 16:52:39 david-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Nov  6 16:52:39 david-desktop dhclient: Listening on LPF/eth0/00:1a:a0:0f:7e:fa
Nov  6 16:52:39 david-desktop dhclient: Sending on   LPF/eth0/00:1a:a0:0f:7e:fa
Nov  6 16:52:39 david-desktop dhclient: Sending on   Socket/fallback
Nov  6 16:52:40 david-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov  6 16:52:40 david-desktop dhclient: DHCPOFFER of 82.139.118.3 from 82.139.112.1
Nov  6 16:52:40 david-desktop dhclient: DHCPREQUEST of 82.139.118.3 on eth0 to 255.255.255.255 port 67
Nov  6 16:52:40 david-desktop dhclient: DHCPACK of 82.139.118.3 from 82.139.112.1
Nov  6 16:52:40 david-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Nov  6 16:52:40 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  6 16:52:40 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov  6 16:52:40 david-desktop NetworkManager: <info>    address 82.139.118.3 
Nov  6 16:52:40 david-desktop NetworkManager: <info>    prefix 21 (255.255.248.0) 
Nov  6 16:52:40 david-desktop NetworkManager: <info>    gateway 82.139.112.1 
Nov  6 16:52:40 david-desktop NetworkManager: <info>    nameserver '82.139.64.64' 
Nov  6 16:52:40 david-desktop NetworkManager: <info>    nameserver '82.139.66.66' 
Nov  6 16:52:40 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  6 16:52:40 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov  6 16:52:40 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov  6 16:52:40 david-desktop avahi-daemon[2830]: Joining mDNS multicast group on interface eth0.IPv4 with address 82.139.118.3.
Nov  6 16:52:40 david-desktop avahi-daemon[2830]: New relevant interface eth0.IPv4 for mDNS.
Nov  6 16:52:40 david-desktop avahi-daemon[2830]: Registering new address record for 82.139.118.3 on eth0.IPv4.
Nov  6 16:52:40 david-desktop dhclient: bound to 82.139.118.3 -- renewal in 1518 seconds.
Nov  6 16:52:41 david-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Nov  6 16:52:41 david-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov  6 16:52:41 david-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov  6 16:52:41 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  6 16:52:42 david-desktop ntpdate[5222]: adjust time server 91.189.94.4 offset -0.054003 sec
Nov  6 16:52:58 david-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Nov  6 16:52:58 david-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Nov  6 16:52:58 david-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40). 
Nov  6 16:52:58 david-desktop NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5163 
Nov  6 16:52:58 david-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Nov  6 16:52:58 david-desktop avahi-daemon[2830]: Withdrawing address record for 82.139.118.3 on eth0.
Nov  6 16:52:58 david-desktop avahi-daemon[2830]: Leaving mDNS multicast group on interface eth0.IPv4 with address 82.139.118.3.
Nov  6 16:52:58 david-desktop avahi-daemon[2830]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov  6 16:53:01 david-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Nov  6 16:53:01 david-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  6 16:53:01 david-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  6 16:53:01 david-desktop dhclient: All rights reserved.
Nov  6 16:53:01 david-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  6 16:53:01 david-desktop dhclient: 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  dhclient started with pid 5239 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Nov  6 16:53:01 david-desktop dhclient: Listening on LPF/eth0/00:1a:a0:0f:7e:fa
Nov  6 16:53:01 david-desktop dhclient: Sending on   LPF/eth0/00:1a:a0:0f:7e:fa
Nov  6 16:53:01 david-desktop dhclient: Sending on   Socket/fallback
Nov  6 16:53:01 david-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 16:53:01 david-desktop dhclient: DHCPOFFER of 82.139.118.3 from 82.139.112.1
Nov  6 16:53:01 david-desktop dhclient: DHCPREQUEST of 82.139.118.3 on eth0 to 255.255.255.255 port 67
Nov  6 16:53:01 david-desktop dhclient: DHCPACK of 82.139.118.3 from 82.139.112.1
Nov  6 16:53:01 david-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>    address 82.139.118.3 
Nov  6 16:53:01 david-desktop NetworkManager: <info>    prefix 21 (255.255.248.0) 
Nov  6 16:53:01 david-desktop NetworkManager: <info>    gateway 82.139.112.1 
Nov  6 16:53:01 david-desktop NetworkManager: <info>    nameserver '82.139.64.64' 
Nov  6 16:53:01 david-desktop NetworkManager: <info>    nameserver '82.139.66.66' 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov  6 16:53:01 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov  6 16:53:01 david-desktop avahi-daemon[2830]: Joining mDNS multicast group on interface eth0.IPv4 with address 82.139.118.3.
Nov  6 16:53:01 david-desktop avahi-daemon[2830]: New relevant interface eth0.IPv4 for mDNS.
Nov  6 16:53:01 david-desktop avahi-daemon[2830]: Registering new address record for 82.139.118.3 on eth0.IPv4.
Nov  6 16:53:01 david-desktop dhclient: bound to 82.139.118.3 -- renewal in 1582 seconds.
Nov  6 16:53:02 david-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Nov  6 16:53:02 david-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov  6 16:53:02 david-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov  6 16:53:02 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  6 16:53:03 david-desktop ntpdate[5296]: adjust time server 91.189.94.4 offset -0.044719 sec
Nov  6 16:53:12 david-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Nov  6 16:53:12 david-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Nov  6 16:53:12 david-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40). 
Nov  6 16:53:12 david-desktop NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5239 
Nov  6 16:53:12 david-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Nov  6 16:53:12 david-desktop avahi-daemon[2830]: Withdrawing address record for 82.139.118.3 on eth0.
Nov  6 16:53:12 david-desktop avahi-daemon[2830]: Leaving mDNS multicast group on interface eth0.IPv4 with address 82.139.118.3.
Nov  6 16:53:12 david-desktop avahi-daemon[2830]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov  6 16:53:14 david-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  dhclient started with pid 5313 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov  6 16:53:14 david-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  6 16:53:14 david-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  6 16:53:14 david-desktop dhclient: All rights reserved.
Nov  6 16:53:14 david-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov  6 16:53:14 david-desktop dhclient: 
Nov  6 16:53:14 david-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Nov  6 16:53:14 david-desktop dhclient: Listening on LPF/eth0/00:1a:a0:0f:7e:fa
Nov  6 16:53:14 david-desktop dhclient: Sending on   LPF/eth0/00:1a:a0:0f:7e:fa
Nov  6 16:53:14 david-desktop dhclient: Sending on   Socket/fallback
Nov  6 16:53:18 david-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov  6 16:53:18 david-desktop dhclient: DHCPOFFER of 82.139.118.3 from 82.139.112.1
Nov  6 16:53:18 david-desktop dhclient: DHCPREQUEST of 82.139.118.3 on eth0 to 255.255.255.255 port 67
Nov  6 16:53:18 david-desktop dhclient: DHCPACK of 82.139.118.3 from 82.139.112.1
Nov  6 16:53:18 david-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Nov  6 16:53:18 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  6 16:53:18 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov  6 16:53:18 david-desktop NetworkManager: <info>    address 82.139.118.3 
Nov  6 16:53:18 david-desktop NetworkManager: <info>    prefix 21 (255.255.248.0) 
Nov  6 16:53:18 david-desktop NetworkManager: <info>    gateway 82.139.112.1 
Nov  6 16:53:18 david-desktop NetworkManager: <info>    nameserver '82.139.64.64' 
Nov  6 16:53:18 david-desktop NetworkManager: <info>    nameserver '82.139.66.66' 
Nov  6 16:53:18 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  6 16:53:18 david-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov  6 16:53:18 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov  6 16:53:18 david-desktop avahi-daemon[2830]: Joining mDNS multicast group on interface eth0.IPv4 with address 82.139.118.3.
Nov  6 16:53:18 david-desktop dhclient: bound to 82.139.118.3 -- renewal in 1412 seconds.
Nov  6 16:53:18 david-desktop avahi-daemon[2830]: New relevant interface eth0.IPv4 for mDNS.
Nov  6 16:53:18 david-desktop avahi-daemon[2830]: Registering new address record for 82.139.118.3 on eth0.IPv4.
Nov  6 16:53:19 david-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Nov  6 16:53:19 david-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov  6 16:53:19 david-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov  6 16:53:19 david-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  6 16:53:19 david-desktop ntpdate[5372]: adjust time server 91.189.94.4 offset -0.037618 sec
```First of all, thanks for the replies! 

@ Earl-Gray: strange enough, torrents aren't that much of a problem, it's more downloading packages and particular sites like hotmail (only when I save my username) and google maps.

@ Shredder12: thank you in advance, I really appreciate your help. Above is a piece of log just after I visited hotmail.com and google.maps and had a few disconnects.

---

### Post by shredder12 on 2009-11-06
Well, I can probably see that network got disconnected a few times. But I really can't figure out why.

nd next time use <code> tags to give such info..it won't consume that much space.

---

### Post by David904 on 2009-11-06
Thanks for the effort! Does anyone else has an idea, or am I just screwed?:p

---

### Post by pendelton on 2009-11-07
Will try this out the next time that it disconnects and post the results. Thanks.

---

