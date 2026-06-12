---
title: "Wired network disconnects at random - 8.10"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by rglover on 2009-03-30
Hello all,

I've been using v.8.10 for some time, and recently my network connection has started misbehaving. It seems to be fairly stable most of the time, particularly when the box is unattended. However, when I am at the computer surfing the web (most particularly, it seems, when I'm watching streaming video or using Google Reader) the connection will drop. It will reconnect shortly thereafter, but it is irritating nonetheless. 

ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:0d:56:bf:94:fc  
          inet addr:10.0.1.118  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:febf:94fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24931312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21719848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1392849844 (1.3 GB)  TX bytes:3804701362 (3.8 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57094613 (57.0 MB)  TX bytes:57094613 (57.0 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:10.0.5.1  Bcast:10.0.5.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet2    Link encap:Ethernet  HWaddr 00:50:56:c0:00:02  
          inet addr:192.168.253.1  Bcast:192.168.253.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Nothing too far out of the ordinary, it would seem. 

syslog output around the time when it disconnects/reconnects:

```
Mar 30 00:51:49 [computerName] dhclient: DHCPREQUEST of 10.0.1.118 on eth0 to 10.0.1.1 port 67
Mar 30 00:51:49 [computerName] dhclient: DHCPACK of 10.0.1.118 from 10.0.1.1
Mar 30 00:51:49 [computerName] dhclient: bound to 10.0.1.118 -- renewal in 5474 seconds.
Mar 30 00:53:20 [computerName] kernel: [1778107.740386] b44: eth0: powering down PHY
Mar 30 00:53:21 [computerName] kernel: [1778108.000109] b44: eth0: Link is down.
Mar 30 00:53:21 [computerName] kernel: [1778108.012236] bridge-eth0: disabling the bridge
Mar 30 00:53:21 [computerName] NetworkManager: <info>  (eth0): carrier now OFF (device state 8) 
Mar 30 00:53:21 [computerName] NetworkManager: <info>  (eth0): device state change: 8 -> 2 
Mar 30 00:53:21 [computerName] NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Mar 30 00:53:21 [computerName] vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001003 
Mar 30 00:53:21 [computerName] vmnetBridge: Stopped bridge eth0 to virtual network 0. 
Mar 30 00:53:21 [computerName] kernel: [1778108.024272] bridge-eth0: down
Mar 30 00:53:21 [computerName] kernel: [1778108.025005] bridge-eth0: detached
Mar 30 00:53:21 [computerName] NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 30360 
Mar 30 00:53:21 [computerName] NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess  
Mar 30 00:53:21 [computerName] avahi-daemon[4504]: Withdrawing address record for 10.0.1.118 on eth0.
Mar 30 00:53:21 [computerName] avahi-daemon[4504]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.1.118.
Mar 30 00:53:21 [computerName] avahi-daemon[4504]: Interface eth0.IPv4 no longer relevant for mDNS.
Mar 30 00:53:24 [computerName] kernel: [1778111.000166] b44: eth0: Link is up at 100 Mbps, full duplex.
Mar 30 00:53:24 [computerName] kernel: [1778111.000172] b44: eth0: Flow control is off for TX and off for RX.
Mar 30 00:53:24 [computerName] NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Mar 30 00:53:24 [computerName] dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 30 00:53:24 [computerName] dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 30 00:53:24 [computerName] dhclient: All rights reserved.
Mar 30 00:53:24 [computerName] dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 30 00:53:24 [computerName] dhclient: 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  dhclient started with pid 21326 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 30 00:53:24 [computerName] NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Mar 30 00:53:24 [computerName] vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00011043 
Mar 30 00:53:24 [computerName] vmnetBridge: Started bridge eth0 to virtual network 0. 
Mar 30 00:53:24 [computerName] kernel: [1778111.037548] /dev/vmnet: open called by PID 5602 (vmnet-bridge)
Mar 30 00:53:24 [computerName] kernel: [1778111.037568] /dev/vmnet: hub 0 does not exist, allocating memory.
Mar 30 00:53:24 [computerName] kernel: [1778111.037583] /dev/vmnet: port on hub 0 successfully opened
Mar 30 00:53:24 [computerName] kernel: [1778111.037599] bridge-eth0: up
Mar 30 00:53:24 [computerName] kernel: [1778111.037606] bridge-eth0: attached
Mar 30 00:53:24 [computerName] dhclient: Listening on LPF/eth0/00:0d:56:bf:94:fc
Mar 30 00:53:24 [computerName] dhclient: Sending on   LPF/eth0/00:0d:56:bf:94:fc
Mar 30 00:53:24 [computerName] dhclient: Sending on   Socket/fallback
Mar 30 00:53:25 [computerName] dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Mar 30 00:53:25 [computerName] dhclient: DHCPOFFER of 10.0.1.118 from 10.0.1.1
Mar 30 00:53:25 [computerName] dhclient: DHCPREQUEST of 10.0.1.118 on eth0 to 255.255.255.255 port 67
Mar 30 00:53:25 [computerName] dhclient: DHCPACK of 10.0.1.118 from 10.0.1.1
Mar 30 00:53:25 [computerName] NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Mar 30 00:53:25 [computerName] NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 30 00:53:25 [computerName] NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Mar 30 00:53:25 [computerName] NetworkManager: <info>    address 10.0.1.118 
Mar 30 00:53:25 [computerName] NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar 30 00:53:25 [computerName] NetworkManager: <info>    gateway 10.0.1.1 
Mar 30 00:53:25 [computerName] NetworkManager: <info>    nameserver '10.0.1.1' 
Mar 30 00:53:25 [computerName] NetworkManager: <info>    domain name '[domainName]' 
Mar 30 00:53:25 [computerName] NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 30 00:53:25 [computerName] NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 30 00:53:25 [computerName] NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 30 00:53:25 [computerName] avahi-daemon[4504]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.118.
Mar 30 00:53:25 [computerName] avahi-daemon[4504]: New relevant interface eth0.IPv4 for mDNS.
Mar 30 00:53:25 [computerName] avahi-daemon[4504]: Registering new address record for 10.0.1.118 on eth0.IPv4.
Mar 30 00:53:25 [computerName] dhclient: bound to 10.0.1.118 -- renewal in 6265 seconds.
Mar 30 00:53:26 [computerName] NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Mar 30 00:53:26 [computerName] NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Mar 30 00:53:26 [computerName] NetworkManager: <info>  Activation (eth0) successful, device activated. 
Mar 30 00:53:26 [computerName] NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 30 00:53:26 [computerName] ntpd[30483]: ntpd exiting on signal 15
Mar 30 00:53:27 [computerName] ntpdate[21411]: adjust time server 91.189.94.4 offset 0.000922 sec
Mar 30 00:53:27 [computerName] ntpd[21449]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:54:48 UTC 2009 (1)
Mar 30 00:53:27 [computerName] ntpd[21450]: precision = 1.000 usec
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #1 wildcard, ::#123 Disabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #2 lo, ::1#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #3 eth0, fe80::20d:56ff:febf:94fc#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #4 vmnet1, fe80::250:56ff:fec0:1#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #5 vmnet2, fe80::250:56ff:fec0:2#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #6 lo, 127.0.0.1#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #7 eth0, 10.0.1.118#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #8 vmnet1, 10.0.5.1#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: Listening on interface #9 vmnet2, 192.168.253.1#123 Enabled
Mar 30 00:53:27 [computerName] ntpd[21450]: kernel time sync status 0040
Mar 30 00:53:27 [computerName] ntpd[21450]: frequency initialized -8.758 PPM from /var/lib/ntp/ntp.drift
```

I don't think it's the VM networking adapters, as the problem occurs whether I have virtual machines running or not. And the internal IP address is an address that the router has reserved specifically for this machine, so I don't think it's an IP conflict. This is a hardwired connection into a wireless router, and the wireless connections on the router have no problem whatsoever. 

So, I'm pretty baffled. I don't see anything in the log output that gives any indication as to why the connection should drop. Everything in the setup appears to be just fine. As I said, the problem seems to recur mostly when streaming video (YouTube, Hulu, etc.) or when making AJAX requests (Switching from one feed to another in Google Reader). 

I'm pretty stymied. I would really appreciate any help anybody has to offer.

Cheers!

---

### Post by rglover on 2009-04-01
Originally, this was just a bump. I want to update a bit though to include that I now also experience disconnections when trying to download large files as well. I'm trying to download an iso image of another linux distribution for a USB drive install that I'm trying, and it won't complete the download. It's very frustrating. 

Seriously, any help at all would be most appreciated.

---

### Post by superprash2003 on 2009-04-01
you could try changing your DNS servers to opendns 208.67.222.222 and 208.67.220.220 .. it may not be a disconnections , it just maybe that your dns servers respond slowly at times..

---

### Post by rglover on 2009-04-01
Hey thanks! That's a good suggestion, and something that definitely needed to be done, but it sadly hasn't resolved the problem. I'm still getting randomly disconnected. 

Any other thoughts?

---

### Post by freonchill on 2009-04-01
did you have this problem before you installed vmware and its networking?

---

### Post by rglover on 2009-04-02
> **freonchill said:**
> excuse the language, but WTF?

I'm frankly as baffled as you are. 

But randomness aside: No, I didn't have this problem pre-VMWare. However, I didn't have this problem until well after installing VMWare either, which leads me to think that the two are unrelated. However, I suppose it's worth a shot to turn VMWare off, disable its networking, and see if that resolves the problem.

EDIT: No such luck. I uninstalled VMWare server, and the problem persists.

---

### Post by Gi0rgi0s on 2009-04-12
Bump.  Same problem.  I'm running  8.10 64 bit, netgear wgt624 v3 router, wired connection, Athlon 3800+ w/ ATI MB.


here are similar problems:

[http://ubuntuforums.org/showthread.php?t=850319](http://ubuntuforums.org/showthread.php?t=850319)
[http://ubuntuforums.org/showthread.php?t=318301](http://ubuntuforums.org/showthread.php?t=318301)
[https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2007-July/017496.html](https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2007-July/017496.html)

---

### Post by Gi0rgi0s on 2009-04-18
I managed to fix this by disabling the Power Management acpid service.

---

### Post by rglover on 2009-04-18
Not so successful for me.

I've tried switching DNS. 
I've tried first disabling, then totally uninstalling VMWare.
I've tried disabling acpid and apmd.

None of those things have worked. 

This problem has made my desktop computer a real pain to use. I'm getting increasingly frustrated with every attempt to fix the problem that has failed, and each time my connection drops out makes me want to use the system less and less.

---

### Post by rglover on 2009-04-28
I upgraded to 9.04 - Jaunty. The problem still occurred. It seems to me to be a bug with the b44 kernel driver. I found similar problems to mine on the bug trackers and forums devoted to other distributions entirely. 

I thought to myself--if it seems to be a problem with the driver, why not try different hardware? 

So I installed an old Netgear NIC that I had lying around. Works great. No longer am I being disconnected from the internet at random.

I hesitate to say that the issue is resolved. This isn't a solution to the problem of the b44 driver dropping the connection. Rather, it's more of a workaround.

Should anyone else have this problem, that's what I would recommend they try first. Use a NIC that isn't made by Broadcomm.

---

