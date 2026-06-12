---
title: "dhclient gets stuck."
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by hijynx on 2009-05-25
Long time reader, first time post. You ladies and gentlemen are fantastic help.

I'm having an issue with (I'm assuming) dhclient when connecting to a wireless network at home/work.

I have to go through a chain of reboots, networking restarts, and deleting/adding networks to get the dhclient to ACTUALLY connect.

This is what my syslog says most of the time while connecting:

```
May 25 21:49:22 serenity dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 25 21:49:22 serenity dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 25 21:49:22 serenity dhclient: All rights reserved.
May 25 21:49:22 serenity dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 25 21:49:22 serenity dhclient: 
May 25 21:49:22 serenity NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
May 25 21:49:22 serenity dhclient: Listening on LPF/wlan0/00:1f:3a:54:b6:ca
May 25 21:49:22 serenity dhclient: Sending on   LPF/wlan0/00:1f:3a:54:b6:ca
May 25 21:49:22 serenity dhclient: Sending on   Socket/fallback
May 25 21:49:23 serenity kernel: [  189.813014] wlan0: no IPv6 routers present
May 25 21:49:26 serenity dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May 25 21:49:31 serenity dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May 25 21:49:37 serenity dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May 25 21:49:50 serenity dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
```Gets stuck on the DHCPDISCOVER and never goes any further.

Now, after a series of reboots and me screaming and swearing at the laptop for awhile, this will EVENTUALLY happen:

```
May 25 21:54:36 serenity dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 25 21:54:36 serenity dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 25 21:54:36 serenity dhclient: All rights reserved.
May 25 21:54:36 serenity dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 25 21:54:36 serenity dhclient: 
May 25 21:54:36 serenity NetworkManager: <info>  dhclient started with pid 4621 
May 25 21:54:36 serenity NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May 25 21:54:36 serenity NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
May 25 21:54:36 serenity dhclient: Listening on LPF/wlan0/00:1f:3a:54:b6:ca
May 25 21:54:36 serenity dhclient: Sending on   LPF/wlan0/00:1f:3a:54:b6:ca
May 25 21:54:36 serenity dhclient: Sending on   Socket/fallback
May 25 21:54:39 serenity dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May 25 21:54:41 serenity dhclient: DHCPOFFER of 192.168.1.124 from 192.168.1.1
May 25 21:54:41 serenity dhclient: DHCPREQUEST of 192.168.1.124 on wlan0 to 255.255.255.255 port 67
May 25 21:54:41 serenity dhclient: DHCPACK of 192.168.1.124 from 192.168.1.1
May 25 21:54:41 serenity NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
May 25 21:54:41 serenity NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 25 21:54:41 serenity NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
May 25 21:54:41 serenity NetworkManager: <info>    address 192.168.1.124 
May 25 21:54:41 serenity NetworkManager: <info>    prefix 24 (255.255.255.0) 
May 25 21:54:41 serenity NetworkManager: <info>    gateway 192.168.1.1 
May 25 21:54:41 serenity NetworkManager: <info>    nameserver '192.168.0.1' 
May 25 21:54:41 serenity NetworkManager: <info>    domain name 'domain_not_set.invalid' 
May 25 21:54:41 serenity NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 25 21:54:41 serenity NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
May 25 21:54:41 serenity NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
May 25 21:54:41 serenity avahi-daemon[3197]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.124.
May 25 21:54:41 serenity avahi-daemon[3197]: New relevant interface wlan0.IPv4 for mDNS.
May 25 21:54:41 serenity avahi-daemon[3197]: Registering new address record for 192.168.1.124 on wlan0.IPv4.
May 25 21:54:41 serenity dhclient: bound to 192.168.1.124 -- renewal in 36002 seconds.
May 25 21:54:42 serenity NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
May 25 21:54:42 serenity NetworkManager: <info>  Policy set 'Auto linksys' (wlan0) as default for routing and DNS. 
May 25 21:54:42 serenity NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May 25 21:54:42 serenity NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
```^^ How do I configure/fix the wireless so it does THIS every time?

It eventually works, but it's just frustrating that my otherwise perfectly functional laptop has this last little hiccup to get over.

---

### Post by superprash2003 on 2009-05-26
post the contents of your /etc/dhcp3/dhclient.conf file

---

### Post by hijynx on 2009-05-26
dhclient.conf:

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by superprash2003 on 2009-05-27
try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

---

### Post by Ubuntu Warrior on 2009-05-27
I also experience this problem and have registered a bug for it on Launchpad. Furthermore I can also not set a static IP address via the Network Manager app and eth0 does not come up with an IP. Output of ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:01:02:04:98:61  
          inet6 addr: fe80::201:2ff:fe04:9861/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2873 (2.8 KB)  TX bytes:468 (468.0 B)
          Interrupt:3 Base address:0x2f80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3424 (3.4 KB)  TX bytes:3424 (3.4 KB)

pan0      Link encap:Ethernet  HWaddr 8a:73:ae:2c:2d:9e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:5b:6f:41:b9  
          inet addr:192.168.168.2  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe6f:41b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:116417169 (116.4 MB)  TX bytes:10936625 (10.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-6F-41-B9-31-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have had to connect a D-Link USB wireless dongle to the HP e-PC to get connectivity going.

---

### Post by SabreWolfy on 2009-05-29
> **superprash2003 said:**
> try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

@superprash:
Thanks! This DHCP issue has really been a frustration for me in Jaunty. I've applied the changes you suggest, so now I'm waiting to see if the problem is resolved.

---

### Post by hijynx on 2009-05-29
> **superprash2003 said:**
> try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

I had this problem in the previous version as well, I tried this solution, but it didn't help :(

---

### Post by SabreWolfy on 2009-05-30
> **hijynx said:**
> I had this problem in the previous version as well, I tried this solution, but it didn't help :(

Oh :-( It's a very frustrating problem -- I have a desktop machine connected by ethernet and it's driving me crazy that it just disconnects eth0. I thought at first it only happened when the connection was idle, but I've SEEN it just drop the connection in front of me while the connection is active.

I lowered the lease time of addresses on the router, but maybe what I should do is increase that time. I'll try that as well. I've removed all references to the rfc3442 thing mentioned in that post (commenting out one line and then deleting some text from another line), so I'm waiting to see if that works for me.

Bugs have been filed already -- I'm surprised -- and a little frustrated -- that this has not been solved yet. It's a serious bug, which renders a machine "dead in the water" and requires physical access to the machine to resolve.

After turning my router off and on again, I noticed that my desktop machine (Jaunty) did NOT automatically obtain and IP address again. However, my Jaunty Server machine did. I think this confirms that the bug is related, once again, to Network Manager, as this is not running, as far as I can tell, in the server version. Possibly this means that a Jaunty Server will not disconnect spontaneously?

I'm planning to try WICD in a few days, when I get some time to look at it.

---

