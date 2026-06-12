---
title: "Wireless disconnects randomly, have to reboot to reconnect"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by thelordx on 2012-11-28
I've got a really annoying problem. I'm running 12.04 on an Lenovo W520. I can connect to wireless networks with no problem, but after an indeterminate amount of time (usually 1-3 days), I get disconnected from the network and then can't reconnect unless I reboot my laptop.  Here's what I see in syslog:

> Nov 28 09:39:24 Ozmodiar wpa_supplicant[1391]: WPA: Group rekeying completed with 00:22:b0:bb:4a:18 [GTK=TKIP]
Nov 28 09:39:58 Ozmodiar wpa_supplicant[1391]: WPA: Group rekeying completed with 00:22:b0:bb:4a:18 [GTK=TKIP]
Nov 28 09:39:59 Ozmodiar wpa_supplicant[1391]: CTRL-EVENT-DISCONNECTED bssid=00:22:b0:bb:4a:18 reason=4
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.084386] cfg80211: All devices are disconnected, going to restore regulatory settings
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.084398] cfg80211: Restoring regulatory settings
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.084408] cfg80211: Calling CRDA to update world regulatory domain
Nov 28 09:40:00 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092621] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092631] cfg80211: World regulatory domain updated:
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092635] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092642] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092648] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092653] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092658] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 28 09:40:00 Ozmodiar kernel: [ 2462.092663] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 28 09:40:00 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 09:40:01 Ozmodiar CRON[4649]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)
Nov 28 09:40:01 Ozmodiar CRON[4650]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Nov 28 09:40:11 Ozmodiar wpa_supplicant[1391]: Trying to authenticate with 84:1b:5e:c9:f2:07 (SSID='THOR Network' freq=2412 MHz)
Nov 28 09:40:11 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 09:40:11 Ozmodiar kernel: [ 2473.591036] wlan0: direct probe to 84:1b:5e:c9:f2:07 (try 1/3)
Nov 28 09:40:11 Ozmodiar kernel: [ 2473.789743] wlan0: direct probe to 84:1b:5e:c9:f2:07 (try 2/3)
Nov 28 09:40:12 Ozmodiar kernel: [ 2473.989427] wlan0: direct probe to 84:1b:5e:c9:f2:07 (try 3/3)
Nov 28 09:40:12 Ozmodiar kernel: [ 2474.189154] wlan0: direct probe to 84:1b:5e:c9:f2:07 timed out
Nov 28 09:40:14 Ozmodiar NetworkManager[1004]: <info> (wlan0): roamed from BSSID 00:22:B0:BB:4A:18 (THOR Network) to (none) ((none))
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <warn> (wlan0): link timed out.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2069
Nov 28 09:40:15 Ozmodiar kernel: [ 2477.336227] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 28 09:40:15 Ozmodiar avahi-daemon[1002]: Withdrawing address record for fe80::224:d7ff:fe97:4c6c on wlan0.
Nov 28 09:40:15 Ozmodiar avahi-daemon[1002]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d7ff:fe97:4c6c.
Nov 28 09:40:15 Ozmodiar avahi-daemon[1002]: Interface wlan0.IPv6 no longer relevant for mDNS.
Nov 28 09:40:15 Ozmodiar avahi-daemon[1002]: Withdrawing address record for 192.168.0.185 on wlan0.
Nov 28 09:40:15 Ozmodiar avahi-daemon[1002]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.185.
Nov 28 09:40:15 Ozmodiar avahi-daemon[1002]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov 28 09:40:15 Ozmodiar dnsmasq[2073]: exiting on receipt of SIGTERM
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> DNS: starting dnsmasq...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 09:40:15 Ozmodiar dnsmasq[4685]: started, version 2.59 cache disabled
Nov 28 09:40:15 Ozmodiar dnsmasq[4685]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Nov 28 09:40:15 Ozmodiar dnsmasq[4685]: warning: no upstream servers configured
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Clearing nscd hosts cache.
Nov 28 09:40:15 Ozmodiar dbus[970]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Auto-activating connection 'THOR Network'.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) starting connection 'THOR Network'
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0/wireless): access point 'THOR Network' has security, but secrets are required.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0/wireless): connection 'THOR Network' has security, and secrets exist.  No new secrets needed.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Config: added 'ssid' value 'THOR Network'
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Config: added 'scan_ssid' value '1'
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Config: added 'psk' value '<omitted>'
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 09:40:15 Ozmodiar NetworkManager[1004]: <info> Config: set interface ap_scan to 1
Nov 28 09:40:15 Ozmodiar dbus[970]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 28 09:40:16 Ozmodiar sm-msp-queue[4672]: My unqualified host name (Ozmodiar) unknown; sleeping for retry
Nov 28 09:40:17 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 09:40:20 Ozmodiar wpa_supplicant[1391]: Trying to authenticate with 84:1b:5e:c9:f2:07 (SSID='THOR Network' freq=2412 MHz)
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.542887] wlan0: direct probe to 84:1b:5e:c9:f2:07 (try 1/3)
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.557977] wlan0: direct probe responded
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.612571] wlan0: authenticate with 84:1b:5e:c9:f2:07 (try 1)
Nov 28 09:40:20 Ozmodiar wpa_supplicant[1391]: Trying to associate with 84:1b:5e:c9:f2:07 (SSID='THOR Network' freq=2412 MHz)
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.622165] wlan0: authenticated
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.688506] wlan0: associate with 84:1b:5e:c9:f2:07 (try 1)
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.754897] wlan0: RX ReassocResp from 84:1b:5e:c9:f2:07 (capab=0x411 status=0 aid=17)
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.754907] wlan0: associated
Nov 28 09:40:20 Ozmodiar wpa_supplicant[1391]: Associated with 84:1b:5e:c9:f2:07
Nov 28 09:40:20 Ozmodiar kernel: [ 2482.764763] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: associating -> associated
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Nov 28 09:40:20 Ozmodiar wpa_supplicant[1391]: WPA: Key negotiation completed with 84:1b:5e:c9:f2:07 [PTK=CCMP GTK=CCMP]
Nov 28 09:40:20 Ozmodiar wpa_supplicant[1391]: CTRL-EVENT-CONNECTED - Connection to 84:1b:5e:c9:f2:07 completed (reauth) [id=0 id_str=]
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'THOR Network'.
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> dhclient started with pid 4714
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 09:40:20 Ozmodiar dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Nov 28 09:40:20 Ozmodiar dhclient: Copyright 2004-2011 Internet Systems Consortium.
Nov 28 09:40:20 Ozmodiar dhclient: All rights reserved.
Nov 28 09:40:20 Ozmodiar dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Nov 28 09:40:20 Ozmodiar dhclient: 
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 09:40:20 Ozmodiar NetworkManager[1004]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 09:40:20 Ozmodiar dhclient: Listening on LPF/wlan0/00:24:d7:97:4c:6c
Nov 28 09:40:20 Ozmodiar dhclient: Sending on   LPF/wlan0/00:24:d7:97:4c:6c
Nov 28 09:40:20 Ozmodiar dhclient: Sending on   Socket/fallback
Nov 28 09:40:20 Ozmodiar dhclient: DHCPREQUEST of 192.168.0.185 on wlan0 to 255.255.255.255 port 67
Nov 28 09:40:22 Ozmodiar avahi-daemon[1002]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::224:d7ff:fe97:4c6c.
Nov 28 09:40:22 Ozmodiar avahi-daemon[1002]: New relevant interface wlan0.IPv6 for mDNS.
Nov 28 09:40:22 Ozmodiar avahi-daemon[1002]: Registering new address record for fe80::224:d7ff:fe97:4c6c on wlan0.*.
Nov 28 09:40:23 Ozmodiar dhclient: DHCPREQUEST of 192.168.0.185 on wlan0 to 255.255.255.255 port 67
Nov 28 09:40:28 Ozmodiar dhclient: DHCPNAK from 192.168.1.1
Nov 28 09:40:28 Ozmodiar NetworkManager[1004]: <info> (wlan0): DHCPv4 state changed preinit -> expire
Nov 28 09:40:28 Ozmodiar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov 28 09:40:28 Ozmodiar NetworkManager[1004]: <info> (wlan0): DHCPv4 state changed expire -> preinit
Nov 28 09:40:31 Ozmodiar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Nov 28 09:40:31 Ozmodiar kernel: [ 2493.464408] wlan0: no IPv6 routers present
Nov 28 09:40:36 Ozmodiar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov 28 09:40:41 Ozmodiar NetworkManager[1004]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 09:40:41 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 09:40:41 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 09:40:41 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 09:40:49 Ozmodiar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov 28 09:41:02 Ozmodiar dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Nov 28 09:41:03 Ozmodiar dhclient: DHCPREQUEST of 192.168.1.27 on wlan0 to 255.255.255.255 port 67
Nov 28 09:41:03 Ozmodiar dhclient: DHCPOFFER of 192.168.1.27 from 192.168.1.1
Nov 28 09:41:03 Ozmodiar dhclient: DHCPACK of 192.168.1.27 from 192.168.1.1
Nov 28 09:41:03 Ozmodiar dhclient: bound to 192.168.1.27 -- renewal in 36012 seconds.
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info>   address 192.168.1.27
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info>   prefix 24 (255.255.255.0)
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info>   gateway 192.168.1.1
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info>   nameserver '192.168.1.1'
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 09:41:03 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 09:41:03 Ozmodiar avahi-daemon[1002]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.27.
Nov 28 09:41:03 Ozmodiar avahi-daemon[1002]: New relevant interface wlan0.IPv4 for mDNS.
Nov 28 09:41:03 Ozmodiar avahi-daemon[1002]: Registering new address record for 192.168.1.27 on wlan0.IPv4.
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> DNS: starting dnsmasq...
Nov 28 09:41:04 Ozmodiar dnsmasq[4685]: exiting on receipt of SIGTERM
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 09:41:04 Ozmodiar dnsmasq[4727]: started, version 2.59 cache disabled
Nov 28 09:41:04 Ozmodiar dnsmasq[4727]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Nov 28 09:41:04 Ozmodiar dnsmasq[4727]: using nameserver 192.168.1.1#53
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> Clearing nscd hosts cache.
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> (wlan0): roamed from BSSID 00:22:B0:BB:4A:18 (THOR Network) to 84:1B:5E:C9:F2:07 (THOR Network)
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> Policy set 'THOR Network' (wlan0) as default for IPv4 routing and DNS.
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) successful, device activated.
Nov 28 09:41:04 Ozmodiar NetworkManager[1004]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 28 09:41:04 Ozmodiar dbus[970]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 28 09:41:04 Ozmodiar dbus[970]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 28 09:41:13 Ozmodiar ntpdate[4775]: adjust time server 91.189.94.4 offset 0.040536 sec
Nov 28 09:41:14 Ozmodiar kernel: [ 2536.775629] CIFS VFS: Error connecting to socket. Aborting operation
Nov 28 09:41:14 Ozmodiar kernel: [ 2536.775830] CIFS VFS: cifs_mount failed w/return code = -115


> lspci: 
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)


I'd be thrilled if someone can point me in the right direction.

---

### Post by thelordx on 2012-11-29
Bump. Anyone have any idea? Any other information I could gather?

---

### Post by thelordx on 2012-12-02
Is this really undiagnosable? No thoughts from anyone?

---

### Post by thelordx on 2012-12-02
Just in case, here's a little more info on wireless hardware:
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:97:4c:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-32-generic firmware=9.221.4.1 build 25532 ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:53 memory:d5300000-d5301fff

---

### Post by awm086 on 2012-12-05
Does this happen on every network? Or on school/work network with multiple access points? I am going through the same issues except my problem happens all day long and wifi refuses to connect to the proper access point.
You may have the same problem. But if you are lucky and you do not have the same problem as I, and if your network have multiple access point, from the command line execute ```
nm-tool
``` this will list all access point 
```
Infra, 00:24:6C:80:D7:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
```
Find the one with the highest strength then open network manager, (from dashboard) click on wireless, click on options, then enter the MAC address (the number after infra in the code above) you see in the result on nm-tool 
see this [http://i.stack.imgur.com/C8Z6w.png](http://i.stack.imgur.com/C8Z6w.png) for reference.

IF this does not help, you may have similar problem as I do. I have my log here [http://pastebin.com/e5324Z0m](http://pastebin.com/e5324Z0m). And it is similar to yours. I am following this hoping they may have an answer for me, you may be interested in it to. [ LINK ]("http://ubuntuforums.org/showthread.php?p=12388686#post12388686")

---

### Post by thelordx on 2012-12-10
It seems to be happening much less on my home network, but more on my work network. However, neither of them have multiple access points.

---

