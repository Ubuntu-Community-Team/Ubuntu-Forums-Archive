---
title: "Wireless not working after upgrade to 12.04"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by spospy on 2012-05-05
Hi,

I recently upgraded to 12.04 and now the wireless connection keeps dropping after a few seconds.
None of my other devices have a problem with my router and vice versa so I can only think it's this latest distribution that is causing the problem.

Here are some details.

```
Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card [144f:7128]
	Kernel driver in use: ath5k

```

And here is the output from my syslog.

```
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) starting connection 'Auto sumpternet'
May  5 14:28:23 ubuntu NetworkManager[895]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  5 14:28:23 ubuntu NetworkManager[895]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0/wireless): access point 'Auto sumpternet' has security, but secrets are required.
May  5 14:28:23 ubuntu NetworkManager[895]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May  5 14:28:23 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  5 14:28:39 ubuntu NetworkManager[895]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  5 14:28:39 ubuntu NetworkManager[895]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  5 14:28:39 ubuntu NetworkManager[895]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0/wireless): connection 'Auto sumpternet' has security, and secrets exist.  No new secrets needed.
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: added 'ssid' value 'sumpternet'
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: added 'scan_ssid' value '1'
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: added 'key_mgmt' value 'NONE'
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: added 'auth_alg' value 'OPEN'
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: added 'wep_key0' value '<omitted>'
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: added 'wep_tx_keyidx' value '0'
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  5 14:28:39 ubuntu NetworkManager[895]: <info> Config: set interface ap_scan to 1
May  5 14:28:39 ubuntu NetworkManager[895]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May  5 14:28:40 ubuntu wpa_supplicant[973]: Trying to authenticate with 00:24:17:95:ed:e7 (SSID='sumpternet' freq=2437 MHz)
May  5 14:28:40 ubuntu kernel: [ 2491.054659] wlan0: authenticate with 00:24:17:95:ed:e7 (try 1)
May  5 14:28:40 ubuntu wpa_supplicant[973]: Trying to associate with 00:24:17:95:ed:e7 (SSID='sumpternet' freq=2437 MHz)
May  5 14:28:40 ubuntu NetworkManager[895]: <info> (wlan0): supplicant interface state: scanning -> authenticating
May  5 14:28:40 ubuntu kernel: [ 2491.057229] wlan0: authenticated
May  5 14:28:40 ubuntu kernel: [ 2491.057403] wlan0: associate with 00:24:17:95:ed:e7 (try 1)
May  5 14:28:40 ubuntu kernel: [ 2491.064038] wlan0: RX ReassocResp from 00:24:17:95:ed:e7 (capab=0x411 status=0 aid=1)
May  5 14:28:40 ubuntu kernel: [ 2491.064043] wlan0: associated
May  5 14:28:40 ubuntu wpa_supplicant[973]: Associated with 00:24:17:95:ed:e7
May  5 14:28:40 ubuntu wpa_supplicant[973]: CTRL-EVENT-CONNECTED - Connection to 00:24:17:95:ed:e7 completed (reauth) [id=0 id_str=]
May  5 14:28:40 ubuntu NetworkManager[895]: <info> (wlan0): supplicant interface state: authenticating -> associating
May  5 14:28:40 ubuntu NetworkManager[895]: <info> (wlan0): supplicant interface state: associating -> completed
May  5 14:28:40 ubuntu NetworkManager[895]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'sumpternet'.
May  5 14:28:40 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May  5 14:28:40 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May  5 14:28:40 ubuntu NetworkManager[895]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  5 14:28:40 ubuntu NetworkManager[895]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May  5 14:28:40 ubuntu NetworkManager[895]: <info> dhclient started with pid 6296
May  5 14:28:40 ubuntu NetworkManager[895]: <info> Activation (wlan0) Beginning IP6 addrconf.
May  5 14:28:40 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May  5 14:28:40 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May  5 14:28:40 ubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
May  5 14:28:40 ubuntu dhclient: All rights reserved.
May  5 14:28:40 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
May  5 14:28:40 ubuntu dhclient: 
May  5 14:28:40 ubuntu NetworkManager[895]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May  5 14:28:40 ubuntu dhclient: Listening on LPF/wlan0/00:24:d2:be:34:e3
May  5 14:28:40 ubuntu dhclient: Sending on   LPF/wlan0/00:24:d2:be:34:e3
May  5 14:28:40 ubuntu dhclient: Sending on   Socket/fallback
May  5 14:28:40 ubuntu dhclient: DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
May  5 14:28:40 ubuntu dhclient: DHCPACK of 192.168.1.65 from 192.168.1.254
May  5 14:28:40 ubuntu dhclient: bound to 192.168.1.65 -- renewal in 41689 seconds.
May  5 14:28:40 ubuntu NetworkManager[895]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
May  5 14:28:41 ubuntu NetworkManager[895]: <info>   address 192.168.1.65
May  5 14:28:41 ubuntu NetworkManager[895]: <info>   prefix 24 (255.255.255.0)
May  5 14:28:41 ubuntu NetworkManager[895]: <info>   gateway 192.168.1.254
May  5 14:28:41 ubuntu NetworkManager[895]: <info>   nameserver '192.168.1.254'
May  5 14:28:41 ubuntu NetworkManager[895]: <info>   domain name 'lan'
May  5 14:28:41 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  5 14:28:41 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May  5 14:28:42 ubuntu NetworkManager[895]: <info> DNS: starting dnsmasq...
May  5 14:28:42 ubuntu dnsmasq[6166]: exiting on receipt of SIGTERM
May  5 14:28:42 ubuntu NetworkManager[895]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
May  5 14:28:42 ubuntu dnsmasq[6301]: started, version 2.59 cache disabled
May  5 14:28:42 ubuntu dnsmasq[6301]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May  5 14:28:42 ubuntu dnsmasq[6301]: using nameserver 192.168.1.254#53
May  5 14:28:42 ubuntu dnsmasq[6301]: using nameserver 192.168.1.254#53
May  5 14:28:42 ubuntu NetworkManager[895]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May  5 14:28:42 ubuntu NetworkManager[895]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May  5 14:28:42 ubuntu NetworkManager[895]: <info> Activation (wlan0) successful, device activated.
May  5 14:28:42 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May  5 14:28:42 ubuntu dbus[844]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  5 14:28:42 ubuntu dbus[844]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  5 14:28:42 ubuntu ntpd[6133]: ntpd exiting on signal 15
May  5 14:28:51 ubuntu kernel: [ 2501.152054] wlan0: no IPv6 routers present
May  5 14:28:53 ubuntu ntpdate[6382]: adjust time server 77.75.105.169 offset -0.001182 sec
May  5 14:28:53 ubuntu ntpd[6411]: ntpd 4.2.6p3@1.2290 Tue Mar  6 15:36:36 UTC 2012 (1)
May  5 14:28:53 ubuntu ntpd[6412]: proto: precision = 1.047 usec
May  5 14:28:53 ubuntu ntpd[6412]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
May  5 14:28:53 ubuntu ntpd[6412]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen and drop on 1 v6wildcard :: UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen normally on 2 lo 127.0.0.1 UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen normally on 3 eth0 192.168.1.64 UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen normally on 4 wlan0 192.168.1.65 UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen normally on 5 wlan0 fe80::224:d2ff:febe:34e3 UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen normally on 6 eth0 fe80::21e:33ff:fed5:83b UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: Listen normally on 7 lo ::1 UDP 123
May  5 14:28:53 ubuntu ntpd[6412]: peers refreshed
May  5 14:28:53 ubuntu ntpd[6412]: Listening on routing socket on fd #24 for interface updates
May  5 14:28:53 ubuntu kernel: [ 2503.748166] type=1400 audit(1336224533.611:45): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/ntpd" name="/etc/likewise-open/user-ignore" pid=6412 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
May  5 14:29:00 ubuntu NetworkManager[895]: <info> (wlan0): IP6 addrconf timed out or failed.
May  5 14:29:00 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  5 14:29:00 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  5 14:29:00 ubuntu NetworkManager[895]: <warn> Activation (wlan0/wireless): could not get IP configuration for connection 'Auto sumpternet'.
May  5 14:29:00 ubuntu NetworkManager[895]: <info> (wlan0): device state change: activated -> need-auth (reason 'none') [100 60 0]
May  5 14:29:00 ubuntu NetworkManager[895]: <info> Activation (wlan0/wireless): asking for new secrets
May  5 14:29:00 ubuntu NetworkManager[895]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  5 14:29:00 ubuntu dbus[844]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  5 14:29:00 ubuntu kernel: [ 2511.128040] wlan0: deauthenticating from 00:24:17:95:ed:e7 by local choice (reason=3)
May  5 14:29:01 ubuntu dbus[844]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  5 14:29:01 ubuntu wpa_supplicant[973]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
May  5 14:29:01 ubuntu NetworkManager[895]: <info> (wlan0): supplicant interface state: completed -> disconnected
May  5 14:29:01 ubuntu kernel: [ 2511.168215] cfg80211: All devices are disconnected, going to restore regulatory settings
May  5 14:29:01 ubuntu kernel: [ 2511.168222] cfg80211: Restoring regulatory settings
May  5 14:29:01 ubuntu kernel: [ 2511.168237] cfg80211: Calling CRDA to update world regulatory domain
May  5 14:29:01 ubuntu kernel: [ 2511.173209] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May  5 14:29:01 ubuntu kernel: [ 2511.173213] cfg80211: World regulatory domain updated:
May  5 14:29:01 ubuntu kernel: [ 2511.173215] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May  5 14:29:01 ubuntu kernel: [ 2511.173219] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  5 14:29:01 ubuntu kernel: [ 2511.173222] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May  5 14:29:01 ubuntu kernel: [ 2511.173225] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May  5 14:29:01 ubuntu kernel: [ 2511.173228] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  5 14:29:01 ubuntu kernel: [ 2511.173231] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May  5 14:31:01 ubuntu NetworkManager[895]: <warn> No agents were available for this request.
May  5 14:31:01 ubuntu NetworkManager[895]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May  5 14:31:01 ubuntu NetworkManager[895]: <warn> Activation (wlan0) failed for access point (sumpternet)
May  5 14:31:01 ubuntu NetworkManager[895]: <info> Marking connection 'Auto sumpternet' invalid.
May  5 14:31:01 ubuntu NetworkManager[895]: <warn> Activation (wlan0) failed.
May  5 14:31:01 ubuntu NetworkManager[895]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May  5 14:31:01 ubuntu NetworkManager[895]: <info> (wlan0): deactivating device (reason 'none') [0]
May  5 14:31:01 ubuntu NetworkManager[895]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 6296
May  5 14:31:01 ubuntu dnsmasq[6301]: exiting on receipt of SIGTERM

```

Does anyone have ideas how I can make this work again?

---

### Post by egruber on 2012-05-05
I went to Network Connections and deleted the entry for the wireless network and then re-added it.  That fixed it for me.

---

### Post by wildmanne39 on 2012-05-05
Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -r ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```
do not reboot if this works we will need to make it permanent.
Thanks

---

### Post by spospy on 2012-05-06
wildmanne39 that didn't work straight away and it threw me off again. However I then tried deleting the existing config and adding it again. This time it has not dropped my connection and seems to be working just fine.

Thanks for you help. How do I now make this permanent?

---

### Post by spospy on 2012-05-06
I added

options ath5k nohwcrypt=1

to

/etc/modprobe.d/ath5k.conf

and this seems to have made the change permanent.

I have rebooted and everything is still working properly.

---

### Post by wildmanne39 on 2012-05-06
Hi, that is how you make it permanent,glad it is working, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by The_Cougar_Kid on 2012-05-09
> **wildmanne39 said:**
> Hi, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -r ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```do not reboot if this works we will need to make it permanent.
Thanks
I am suffering from the same problem.  There are 4 computers in this household; the first three upgraded to 12.04 without issues.  On the 4th - my main day-to-day computer so very important - the wireless connection failed on restart.  I tried the simple suggestion - delete and recreate the network connection - that didn't work.  I tried this suggestion and it failed at the first hurdle - "wlan0: ERROR while getting interface flags: No such device."  Any ideas?

---

### Post by docmayhem on 2012-09-01
I had a similar problem upgrading from 10.04 to 12.04 - losing connection and re-entering the key every 60-90 seconds.

I went into edit connections, selected the proper connection under wireless, resaved the key, and checked "available to all users"

So far, so good.

---

### Post by cleopatra on 2012-12-07
> **spospy said:**
> I added

options ath5k nohwcrypt=1

to

/etc/modprobe.d/ath5k.conf

and this seems to have made the change permanent.

I have rebooted and everything is still working properly.

I have the same problem, want to try your solution, too. However, I don't have ath5k.conf in that directory. what should I edit?

$ ls -ltr
total 44
-rw-r--r-- 1 root root   16 Jan  6  2010 libpisock9.conf
-rw-r--r-- 1 root root  156 Jan 28  2010 blacklist-modem.conf
-rw-r--r-- 1 root root 1077 Apr 13  2010 blacklist-watchdog.conf
-rw-r--r-- 1 root root 1603 Apr 13  2010 blacklist.conf
-rw-r--r-- 1 root root  325 Apr 13  2010 blacklist-ath_pci.conf
-rw-r--r-- 1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root 2507 Feb 15  2012 alsa-base.conf
-rw-r--r-- 1 root root  127 Apr 22  2012 dkms.conf
-rw-r--r-- 1 root root   30 May 18  2012 vmwgfx-fbdev.conf
lrwxrwxrwx 1 root root   41 Nov 13 11:25 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf


this is my config, i have ath9k. Any ideas?

$ sudo lshw -c network
[sudo] password for yang: 
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 20:6a:8a:30:42:d2
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f0400000-f043ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:41:2f:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-32-generic firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff

---

### Post by gutterwomb on 2013-04-09
> **spospy said:**
> I added

options ath5k nohwcrypt=1

to

/etc/modprobe.d/ath5k.conf

and this seems to have made the change permanent.

I have rebooted and everything is still working properly.
Sorry Im a total newbie on using ubuntu. 
The temporary solution worked and its been running fine for past 10min. But I didnt get how to make it permanent. I have no idea what the quoted post means. If you can write it step by step that would prolly clear my confusions.
Thanks in advance

---

