---
title: "ipw2200 connects, gets IP, but doesn't route"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by BaddestCross on 2010-12-21
I'm trying to get this Thinkpad R52 up and running with Maverick but I can't get this beat.  The card gets assigned an IP and I'm not seeing any errors in any of the logs.  I can ping the router once (about 3 or 4 pings come back) at first boot but then it cannot reach the host after that.  I tried with WEP, WPA, and no security enabled.  I'm stumped.  Please help!

---

### Post by chili555 on 2010-12-22
May we have a peek at:```
ping -c5 www.google.com
iwconfig eth1
dmesg | grep -e ipw -e eth1
sudo cat /var/log/syslog | grep -i network
```The last command is likely to produce many lines of output; instead of posting 200 lines here, look for the spot where the connection drops and post the 6-8 lines that illustrate the drop.

Please obscure any personally identifiable information including MAC addresses.

---

### Post by BaddestCross on 2010-12-22
Per your request ...


```
PING www.l.google.com (66.102.7.99) 56(84) bytes of data.
64 bytes from lax04s01-in-f99.1e100.net (66.102.7.99): icmp_req=1 ttl=52 time=15.4 ms
64 bytes from lax04s01-in-f99.1e100.net (66.102.7.99): icmp_req=2 ttl=52 time=40.0 ms
64 bytes from lax04s01-in-f99.1e100.net (66.102.7.99): icmp_req=3 ttl=52 time=30.5 ms
64 bytes from lax04s01-in-f99.1e100.net (66.102.7.99): icmp_req=4 ttl=52 time=31.7 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4006ms
rtt min/avg/max/mdev = 15.458/29.444/40.032/8.865 ms
``````
eth1      IEEE 802.11bg  ESSID:"JEM Group"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <removed>   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:0   Missed beacon:1

``````
[   17.505851] libipw: 802.11 data/management/control stack, git-1.1.13
[   17.505856] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.567239] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.567244] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.567371] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.594374] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.155987] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   29.680023] eth1: no IPv6 routers present
```
I cut out a lot of the syslog output, but I'm including more than you asked for since there are a couple of items in there relating to wpa_supplicant that may be relevant ...

```

     NetworkManager[847]: <info> NetworkManager (version 0.8.1) is starting...
     NetworkManager[847]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
     NetworkManager[847]: <info> trying to start the modem manager...
     NetworkManager[847]: <info> monitoring kernel firmware directory '/lib/firmware'.
     NetworkManager[847]:    SCPlugin-Ifupdown: init!
     NetworkManager[847]:    SCPlugin-Ifupdown: update_system_hostname
     NetworkManager[847]:    SCPluginIfupdown: management mode: unmanaged
     NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
     NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
     NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:04:02.0/net/eth1, iface: eth1)
     NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:04:02.0/net/eth1, iface: eth1): no ifupdown configuration found.
     NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
     NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
     NetworkManager[847]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
     NetworkManager[847]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
     NetworkManager[847]:    SCPlugin-Ifupdown: end _init.
     NetworkManager[847]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
     NetworkManager[847]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
     NetworkManager[847]:    Ifupdown: get unmanaged devices count: 0
     NetworkManager[847]:    SCPlugin-Ifupdown: (135806800) ... get_connections.
     NetworkManager[847]:    SCPlugin-Ifupdown: (135806800) ... get_connections (managed=false): return empty list.
     kernel: [   17.405444] type=1400 audit(1293068238.303:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=599 comm="apparmor_parser"
     kernel: [   17.567239] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
     kernel: [   17.594374] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
     NetworkManager[847]:    Ifupdown: get unmanaged devices count: 0
     NetworkManager[847]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:04:02.0/ieee80211/phy0/rfkill0) (driver <unknown>)
     NetworkManager[847]: <info> WiFi enabled by radio killswitch; enabled by state file
     NetworkManager[847]: <info> WWAN enabled by radio killswitch; enabled by state file
     NetworkManager[847]: <info> WiMAX enabled by radio killswitch; enabled by state file
     NetworkManager[847]: <info> Networking is enabled by state file
     avahi-daemon[854]: Network interface enumeration completed.
     NetworkManager[847]: <info> (eth1): driver supports SSID scans (scan_capa 0x21).
     NetworkManager[847]: <info> (eth1): new 802.11 WiFi device (driver: 'ipw2200' ifindex: 4)
     NetworkManager[847]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
     NetworkManager[847]: <info> (eth1): now managed
     NetworkManager[847]: <info> (eth1): device state change: 1 -> 2 (reason 2)
     NetworkManager[847]: <info> (eth1): bringing up device.
     NetworkManager[847]: <info> (eth1): preparing device.
     NetworkManager[847]: <info> (eth1): deactivating device (reason: 2).
     NetworkManager[847]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
     NetworkManager[847]: <info> modem-manager is now available
     NetworkManager[847]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
     NetworkManager[847]: <info> Trying to start the supplicant...
     NetworkManager[847]: <info> (eth1): supplicant manager state:  down -> idle
     NetworkManager[847]: <info> (eth1): device state change: 2 -> 3 (reason 0)
     NetworkManager[847]: <info> (eth1): supplicant interface state:  starting -> ready
     NetworkManager[847]: <info> Activation (eth1) starting connection 'James' House'
     NetworkManager[847]: <info> (eth1): device state change: 3 -> 4 (reason 0)
     NetworkManager[847]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
     NetworkManager[847]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
     NetworkManager[847]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
     NetworkManager[847]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
     NetworkManager[847]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
     NetworkManager[847]: <info> (eth1): device state change: 4 -> 5 (reason 0)
     NetworkManager[847]: <info> Activation (eth1/wireless): connection 'James' House' has security, and secrets exist.  No new secrets needed.
     NetworkManager[847]: <info> Config: added 'ssid' value 'JEM Group'
     NetworkManager[847]: <info> Config: added 'scan_ssid' value '1'
     NetworkManager[847]: <info> Config: added 'key_mgmt' value 'NONE'
     NetworkManager[847]: <info> Config: added 'auth_alg' value 'OPEN'
     NetworkManager[847]: <info> Config: added 'wep_key0' value '<omitted>'
     NetworkManager[847]: <info> Config: added 'wep_tx_keyidx' value '0'
     NetworkManager[847]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
     NetworkManager[847]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
     NetworkManager[847]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
     NetworkManager[847]: <info> (eth1): supplicant connection state:  scanning -> disconnected
     NetworkManager[847]: <info> Config: set interface ap_scan to 1
     NetworkManager[847]: <info> (eth1): supplicant connection state:  disconnected -> scanning
     NetworkManager[847]: <info> (eth1): supplicant connection state:  scanning -> associating
     NetworkManager[847]: <info> (eth1): supplicant connection state:  associating -> associated
     NetworkManager[847]: <info> (eth1): supplicant connection state:  associated -> completed
     NetworkManager[847]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'JEM Group'.
     NetworkManager[847]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
     NetworkManager[847]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
     NetworkManager[847]: <info> (eth1): device state change: 5 -> 7 (reason 0)
     NetworkManager[847]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
     NetworkManager[847]: <info> dhclient started with pid 1153
     NetworkManager[847]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
     NetworkManager[847]: <info> (eth1): DHCPv4 state changed nbi -> preinit
     NetworkManager[847]: <info> (eth1): DHCPv4 state changed preinit -> bound
     NetworkManager[847]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
     NetworkManager[847]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
     NetworkManager[847]: <info>   address 192.168.2.110
     NetworkManager[847]: <info>   prefix 24 (255.255.255.0)
     NetworkManager[847]: <info>   gateway 192.168.2.1
     NetworkManager[847]: <info>   nameserver '208.67.222.222'
     NetworkManager[847]: <info>   nameserver '208.67.220.220'
     NetworkManager[847]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
     NetworkManager[847]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
     NetworkManager[847]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Dec 22 17:37:24   NetworkManager[847]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Dec 22 17:37:24   NetworkManager[847]: <info> Policy set 'James' House' (eth1) as default for IPv4 routing and DNS.
Dec 22 17:37:24   NetworkManager[847]: <info> Updating /etc/hosts with new system hostname
     NetworkManager[847]: <info> Activation (eth1) successful, device activated.
     NetworkManager[847]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
     nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
     NetworkManager[847]: <error> [1293068252.550288] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
     NetworkManager[847]: <error> [1293068252.578802] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
     NetworkManager[847]: <info> (eth1): supplicant connection state:  completed -> disconnected
     NetworkManager[847]: <info> (eth1): supplicant connection state:  disconnected -> scanning
     NetworkManager[847]: <info> (eth1): supplicant connection state:  scanning -> associating
     NetworkManager[847]: <info> (eth1): supplicant connection state:  associating -> associated
     NetworkManager[847]: <info> (eth1): supplicant connection state:  associated -> completed
     NetworkManager[847]: <info> (eth1): supplicant connection state:  completed -> disconnected
     NetworkManager[847]: <info> (eth1): supplicant connection state:  disconnected -> scanning
     NetworkManager[847]: <info> (eth1): supplicant connection state:  scanning -> associating
     NetworkManager[847]: <info> (eth1): supplicant connection state:  associating -> associated
     NetworkManager[847]: <info> (eth1): supplicant connection state:  associated -> completed
```


Thanks so much for your time.

---

### Post by chili555 on 2010-12-23
> nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failedI have seen this quite a few times; I have googled it quite a few times, but I have never found out what it means or how to fix it.

I saw this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366217?comments=all](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/366217?comments=all)> I just want to add that I eventually did find the source of the problem for all of my issues. It appears that some new neighbors moved in to my building and began broadcasting their wireless on the same frequency as me. Luckily I am running the Tomato firmware on my router, so I was able to see the congestion and switch to a portion of the frequency that no one was on.

Once I did this, my connectivity issues with Ubuntu, and the speed issues with Windows' wireless disappeared.You might do:```
sudo iwlist eth1 scan
```Do you have some nearby networks on the same channel? Can you try moving the router to another channel? I have the best luck on channel 11; I'm the only router on channel 11 that I can scan or Kismet.

There are various parameters that can be used with the ipw2200 driver to get it to operate differently. One is to let the chipset do the encryption, rather than software (wpa_supplicant). Let's try this temporarily. Please do:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
```This will disappear at reboot unless we write a configuration file. Please try it and see if there is any improvement.

---

### Post by BaddestCross on 2010-12-23
Tried it with no difference.  Also, as I mentioned in the OP, the same issue exists when all security is disabled at the router.  I have several other wifi devices that connect and route with no problem.

The thing that really throws me off is that the ThinkPad connects and the router assigns it an IP (that is never lost).

---

### Post by BaddestCross on 2010-12-23
Okay, so I checked the router again, and I guess the TP is dropping the connection but for some reason doesn't realize the connection has been lost.

It does show up and is assigned the IP but goes away from the attached devices list after the 4 pings as shown before.  However, the TP still acts like it's connected and I don't see any logs that are showing otherwise.

---

### Post by BaddestCross on 2010-12-23
I took the machine over to Mickey D's and it connected to their WiFi system and surfed just fine.  It's gotta be an issue with the security OR it just doesn't like my router for some reason.

---

### Post by chili555 on 2010-12-24
I hate to blame the hardware but my ipw2200 works with every network, home or away, WPA, WEP or open with no more than the default tools; Network Manager and wpa_supplicant. The fact that you can connect correctly elsewhere suggests, but does not prove, that it's an issue or setting within your router

---

