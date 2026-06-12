---
title: "wireless connection keeps disconnecting"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by GuruMadMat on 2010-01-07
I have a problem in ubuntu where my wireless connection keeps disconnecting.

when i connect and fill in my wpa/wpa2 password it connects and i get my IP address.

```

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:15:6a:65  
          inet addr:10.0.0.109  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:e8ff:fe15:6a65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88483 (88.4 KB)  TX bytes:41117 (41.1 KB)


```

but then after a while (50 seconds) it says the connection has been terminated. 

my wireless router is a sitecom but is only configured as a gateway.
because my ubuntu server is router and dhcp server.
I have no problem on windows nor on my nintendo wii, which also connects with this router.

only on Ubuntu 9.10 Karmic Koala i have this problem.
my network card is:
```

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


```


Daemon.log:
```

Jan  8 00:16:05 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) starting connection 'Auto D-Link Xtreme N'
Jan  8 00:16:18 asus NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  8 00:16:18 asus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto D-Link Xtreme N' has security, and secrets exist.  No new secrets needed.
Jan  8 00:16:18 asus NetworkManager: <info>  Config: added 'ssid' value 'D-Link Xtreme N'
Jan  8 00:16:18 asus NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan  8 00:16:18 asus NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan  8 00:16:18 asus NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan  8 00:16:18 asus NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  8 00:16:18 asus NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  8 00:16:18 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  8 00:16:18 asus NetworkManager: <info>  Config: set interface ap_scan to 1
Jan  8 00:16:18 asus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  8 00:16:18 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 00:16:20 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:16:20 asus wpa_supplicant[1377]: WPS-AP-AVAILABLE 
Jan  8 00:16:20 asus wpa_supplicant[1377]: Trying to associate with 00:0c:f6:30:3e:61 (SSID='D-Link Xtreme N' freq=2427 MHz)
Jan  8 00:16:20 asus wpa_supplicant[1377]: Association request to the driver failed
Jan  8 00:16:20 asus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan  8 00:16:20 asus wpa_supplicant[1377]: Associated with 00:0c:f6:30:3e:61
Jan  8 00:16:20 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan  8 00:16:20 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan  8 00:16:21 asus NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan  8 00:16:21 asus wpa_supplicant[1377]: WPA: Key negotiation completed with 00:0c:f6:30:3e:61 [PTK=TKIP GTK=TKIP]
Jan  8 00:16:21 asus wpa_supplicant[1377]: CTRL-EVENT-CONNECTED - Connection to 00:0c:f6:30:3e:61 completed (reauth) [id=16 id_str=]
Jan  8 00:16:21 asus NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'D-Link Xtreme N'.
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  8 00:16:21 asus NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jan  8 00:16:21 asus dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  8 00:16:21 asus dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  8 00:16:21 asus dhclient: All rights reserved.
Jan  8 00:16:21 asus dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan  8 00:16:21 asus dhclient: 
Jan  8 00:16:21 asus NetworkManager: <info>  dhclient started with pid 5174
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jan  8 00:16:21 asus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan  8 00:16:21 asus NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jan  8 00:16:21 asus dhclient: Listening on LPF/wlan0/00:13:e8:15:6a:65
Jan  8 00:16:21 asus dhclient: Sending on   LPF/wlan0/00:13:e8:15:6a:65
Jan  8 00:16:21 asus dhclient: Sending on   Socket/fallback
Jan  8 00:16:22 asus dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  8 00:16:22 asus dhclient: DHCPOFFER of 10.0.0.109 from 10.0.0.1
Jan  8 00:16:22 asus dhclient: DHCPREQUEST of 10.0.0.109 on wlan0 to 255.255.255.255 port 67
Jan  8 00:16:22 asus dhclient: DHCPACK of 10.0.0.109 from 10.0.0.1
Jan  8 00:16:22 asus dhclient: bound to 10.0.0.109 -- renewal in 277 seconds.
Jan  8 00:16:22 asus NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
Jan  8 00:16:22 asus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  8 00:16:22 asus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan  8 00:16:22 asus NetworkManager: <info>    address 10.0.0.109
Jan  8 00:16:22 asus NetworkManager: <info>    prefix 8 (255.0.0.0)
Jan  8 00:16:22 asus NetworkManager: <info>    gateway 10.0.0.1
Jan  8 00:16:22 asus NetworkManager: <info>    nameserver '195.130.130.133'
Jan  8 00:16:22 asus NetworkManager: <info>    nameserver '195.130.131.133'
Jan  8 00:16:22 asus NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  8 00:16:22 asus NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  8 00:16:22 asus NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan  8 00:16:22 asus avahi-daemon[955]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.109.
Jan  8 00:16:22 asus avahi-daemon[955]: New relevant interface wlan0.IPv4 for mDNS.
Jan  8 00:16:22 asus avahi-daemon[955]: Registering new address record for 10.0.0.109 on wlan0.IPv4.
Jan  8 00:16:23 asus NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan  8 00:16:23 asus NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jan  8 00:16:23 asus NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jan  8 00:16:23 asus NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan  8 00:16:23 asus ntpdate[5225]: adjust time server 91.189.94.4 offset -0.001725 sec
Jan  8 00:17:05 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:17:05 asus wpa_supplicant[1377]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 00:17:05 asus NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jan  8 00:17:05 asus wpa_supplicant[1377]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 00:17:05 asus wpa_supplicant[1377]: last message repeated 10 times
Jan  8 00:17:05 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 00:17:07 asus wpa_supplicant[1377]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 00:17:07 asus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  8 00:17:09 asus NetworkManager: <debug> [1262906229.002239] periodic_update(): Roamed from BSSID 00:0C:F6:30:3E:61 (D-Link Xtreme N) to (none) ((none))
Jan  8 00:17:10 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:17:10 asus wpa_supplicant[1377]: WPS-AP-AVAILABLE 
Jan  8 00:17:10 asus wpa_supplicant[1377]: Trying to associate with 00:0c:f6:30:3e:61 (SSID='D-Link Xtreme N' freq=2427 MHz)
Jan  8 00:17:10 asus wpa_supplicant[1377]: Association request to the driver failed
Jan  8 00:17:10 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Jan  8 00:17:10 asus wpa_supplicant[1377]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 00:17:10 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan  8 00:17:15 asus wpa_supplicant[1377]: Authentication with 00:00:00:00:00:00 timed out.
Jan  8 00:17:15 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 00:17:17 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:17:17 asus wpa_supplicant[1377]: WPS-AP-AVAILABLE 
Jan  8 00:17:17 asus wpa_supplicant[1377]: Trying to associate with 00:0c:f6:30:3e:61 (SSID='D-Link Xtreme N' freq=2427 MHz)
Jan  8 00:17:17 asus wpa_supplicant[1377]: Association request to the driver failed
Jan  8 00:17:17 asus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan  8 00:17:17 asus wpa_supplicant[1377]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 00:17:17 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 5174
Jan  8 00:17:21 asus avahi-daemon[955]: Withdrawing address record for 10.0.0.109 on wlan0.
Jan  8 00:17:21 asus avahi-daemon[955]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.109.
Jan  8 00:17:21 asus avahi-daemon[955]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  8 00:17:21 asus NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) starting connection 'Auto D-Link Xtreme N'
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto D-Link Xtreme N' has security, but secrets are required.
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto D-Link Xtreme N' has security, and secrets exist.  No new secrets needed.
Jan  8 00:17:21 asus NetworkManager: <info>  Config: added 'ssid' value 'D-Link Xtreme N'
Jan  8 00:17:21 asus NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan  8 00:17:21 asus NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jan  8 00:17:21 asus NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jan  8 00:17:21 asus NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  8 00:17:21 asus NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  8 00:17:21 asus NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  8 00:17:21 asus NetworkManager: <info>  Config: set interface ap_scan to 1
Jan  8 00:17:21 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 00:17:22 asus wpa_supplicant[1377]: Authentication with 00:00:00:00:00:00 timed out.
Jan  8 00:17:22 asus wpa_supplicant[1377]: Failed to initiate AP scan.
Jan  8 00:17:22 asus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  8 00:17:22 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 00:17:23 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:17:23 asus wpa_supplicant[1377]: Trying to associate with 00:0c:f6:30:3e:61 (SSID='D-Link Xtreme N' freq=2427 MHz)
Jan  8 00:17:23 asus wpa_supplicant[1377]: Association request to the driver failed
Jan  8 00:17:23 asus NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan  8 00:17:24 asus wpa_supplicant[1377]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 00:17:24 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan  8 00:17:28 asus wpa_supplicant[1377]: Authentication with 00:00:00:00:00:00 timed out.
Jan  8 00:17:28 asus NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 00:17:30 asus wpa_supplicant[1377]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 00:17:30 asus wpa_supplicant[1377]: Trying to associate with 00:0c:f6:30:3e:61 (SSID='D-Link Xtreme N' freq=2427 MHz)
Jan  8 00:17:30 asus wpa_supplicant[1377]: Association request to the driver failed
...
...

```

I also noticed that when i connect with my laptop and the connection disconnected my wii disconnected as well. so my laptop is causing my wireless router to shutdown or something.

when i connect with a windows laptop i have no problems at all.

---

### Post by CJay554 on 2010-02-12
I have the same card, and i am experiencing the same exact problem, though mine is even worse. It seems that i can connect when i boot the computer, but after a few seconds/minutes, i try to reconnect but it just tries to get an AP address from router (WPA) and just hangs over and over.

This problem definately exists because i've seen many people have the exact same problem, its something with the intel driver and the kernel mixing, its said that the iwl4965 driver works on kernels 2.6.25 and earlier, but after that it began to do this...

Can anyone help? Im trying to convert a windows user to Ubuntu but this is definately going to be an obstacle...

---

### Post by .dave on 2010-11-23
I'm getting issues as well.

This seems to be a big problem for people at the moment. It's a real  shame as I normally rate Ubuntu highly for people looking for a Windoze  alternative. But  I can't recommend it to the 'infirm' if they are going  to have constant battles to get their internet working.

Hope to see a fix soon.

--------------------------------------------------------------------------------

Has anyone tried this solution with any success? [http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/](http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/)

>  **[ubuntu] Lucid Lynx Wireless Keep Dropping (updated)]("http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/")**

   				 					10 					05 					2010 				 					 				  					After enduring the endless wireless disconnection after  upgrading to Ubuntu 10.04 (Lucid Lynx) I have finally found the  solution!
 The symptoms I was seeing is as such:
 
[LIST=1]
[*]connected
[*]after using for 5 minutes to 10 minutes, the wireless network manager get disconnected
[*]only wireless connection selectable is the last network you connect to
[*]unable to re-connect, even after 10 minutes
[*]you must disable the wireless and enable it before you can try to reconnect&#8230;
[*]then back to step 1
[/LIST]
 The steps below worked for me [IMG]http://s2.wp.com/wp-includes/images/smilies/icon_smile.gif?m=1285254906g[/IMG] 
 
[LIST]
[*] *sudo gedit /etc/NetworkManager/nm-system-settings.conf*
[*] set the &#8220;[ifupdown] managed=false&#8221; to true.
[/LIST]
 Although the above changes reduced the frequency of the wireless  drop, but I am still facing it. After thinking it around a bit more,  it&#8217;s more stable now. Below are what I have done:
 
[LIST]
[*]*sudo gedit /etc/NetworkManager/nm-system-settings.conf*
[/LIST]
 
[LIST]
[*]Changed the file to:
[/LIST]
 [INDENT][main]
plugins=ifupdown,keyfile
 [ifupdown]
managed=true
 [ifdown]
managed=true
 [ifup]
managed=true
[/INDENT] Good luck to you! And have fun with Lucid Lynx. Let me know if this  works or if there are other better fix!
 *Added on June 28, 2010:*
 *With with the fixes above, it has only lessen the problem on my  machine and not totally eliminate it. Thanks for the comments on trying  out wicd, which i did give it a try. BUT although the wireless  connection didn&#8217;t drop at all for the 2 days which i have been using it,  i see a cap on the wireless transmission rate of 60KB/s (even after  trying &#8220;sudo iwconfig wlan0 rate 54M&#8221;, which is not the problem*[I]).  This is not acceptable to me, which is why i sent back to using gnome  network manager, but for those of you who want to try out wicd, below  are the commands:
[/I]
 [INDENT]*sudo apt-get install wicd*
 [I]sudo apt-get remove network-manager
[/I]
[/INDENT] *Drop me a message if you have a solution to the transmission rate cap!*
 				
 

---

Good luck and hopefully we'll all find a solution eventually.

---

### Post by mvalero on 2010-11-24
Another solution?

Have a look here:
[http://ubuntuforums.org/showthread.php?p=10159871#post10159871]("http://ubuntuforums.org/showthread.php?p=10159871#post10159871")

It sure helps

---

