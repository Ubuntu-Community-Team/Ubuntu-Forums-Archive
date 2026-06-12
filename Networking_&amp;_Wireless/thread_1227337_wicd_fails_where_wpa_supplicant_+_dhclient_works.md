---
title: "wicd fails where wpa_supplicant + dhclient works??"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by emmiesix on 2009-07-30
I have been trying to get my laptop to connect to a very locked-down wifi at school.  I can finally get access by using

```
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf
sudo dhclient eth1

```

It's a WPA2 network.  I've included the wpa_supplicant.conf and peap-tkip files which I had to tweak to get this far.

When I try to connect using wicd (selecting peap-tkip), it fails.  The logs are not very informative, unfortunately:

```
2009/07/30 13:36:39 :: ---------------------------
2009/07/30 13:36:39 :: wicd initializing...
2009/07/30 13:36:39 :: ---------------------------
2009/07/30 13:36:40 :: Automatically detected wireless interface eth1
2009/07/30 13:36:40 :: found wireless_interface in configuration eth1
2009/07/30 13:36:40 :: setting wireless interface eth1
2009/07/30 13:36:40 :: automatically detected wired interface eth0
2009/07/30 13:36:40 :: found wired_interface in configuration eth0
2009/07/30 13:36:40 :: setting wired interface eth0
2009/07/30 13:36:40 :: found wpa_driver in configuration ndiswrapper
2009/07/30 13:36:40 :: setting wpa driver ndiswrapper
2009/07/30 13:36:40 :: found always_show_wired_interface in configuration False
2009/07/30 13:36:40 :: found use_global_dns in configuration False
2009/07/30 13:36:40 :: setting use global dns to False
2009/07/30 13:36:40 :: setting use global dns to boolean False
2009/07/30 13:36:40 :: found global_dns_1 in configuration None
2009/07/30 13:36:40 :: found global_dns_2 in configuration None
2009/07/30 13:36:40 :: found global_dns_3 in configuration None
2009/07/30 13:36:40 :: setting global dns
2009/07/30 13:36:40 :: global dns servers are None None None
2009/07/30 13:36:40 :: found auto_reconnect in configuration True
2009/07/30 13:36:40 :: setting automatically reconnect when connection drops
2009/07/30 13:36:40 :: found debug_mode in configuration 0
2009/07/30 13:36:40 :: found wired_connect_mode in configuration 1
2009/07/30 13:36:40 :: found signal_display_type in configuration 0
2009/07/30 13:36:40 :: found dhcp_client in configuration 0
2009/07/30 13:36:40 :: Setting dhcp client to 0
2009/07/30 13:36:40 :: found link_detect_tool in configuration 0
2009/07/30 13:36:40 :: found flush_tool in configuration 0
2009/07/30 13:36:40 :: Wireless configuration file found...
2009/07/30 13:36:40 :: Wired configuration file found...
2009/07/30 13:36:40 :: chmoding configuration files 0600...
2009/07/30 13:36:40 :: chowning configuration files root:root...
2009/07/30 13:36:40 :: Using wired interface...eth0
2009/07/30 13:36:40 :: Using wireless interface...eth1
2009/07/30 13:36:40 :: autoconnecting... eth1
2009/07/30 13:36:43 :: No wired connection present, attempting to autoconnect to wireless network
2009/07/30 13:36:43 :: trying to automatically connect to...***
2009/07/30 13:36:43 :: Connecting to wireless network ***
2009/07/30 13:36:43 :: Putting interface down
2009/07/30 13:36:43 :: Releasing DHCP leases...
2009/07/30 13:36:43 :: Setting false IP...
2009/07/30 13:36:43 :: Stopping wpa_supplicant and any DHCP clients
2009/07/30 13:36:43 :: Flushing the routing table...
2009/07/30 13:36:43 :: Generating psk...
2009/07/30 13:36:44 :: WARNING: PSK generation failed!  Falling back to wireless key.
2009/07/30 13:36:44 :: Please report this error to the wicd developers!
2009/07/30 13:36:44 :: Attempting to authenticate...
2009/07/30 13:36:44 :: Putting interface up...
2009/07/30 13:36:44 :: Failed to find status in wpa_cli result 
2009/07/30 13:36:44 :: exiting connection thread
2009/07/30 13:36:50 :: No wired connection present, attempting to autoconnect to wireless network
2009/07/30 13:36:50 :: trying to automatically connect to...***
2009/07/30 13:36:50 :: Connecting to wireless network ***
2009/07/30 13:36:50 :: Putting interface down
2009/07/30 13:36:50 :: Releasing DHCP leases...
2009/07/30 13:36:50 :: Setting false IP...
2009/07/30 13:36:50 :: Stopping wpa_supplicant and any DHCP clients
2009/07/30 13:36:50 :: Flushing the routing table...
2009/07/30 13:36:50 :: Generating psk...
2009/07/30 13:36:50 :: WARNING: PSK generation failed!  Falling back to wireless key.
2009/07/30 13:36:50 :: Please report this error to the wicd developers!
2009/07/30 13:36:50 :: Attempting to authenticate...
2009/07/30 13:36:50 :: Putting interface up...
2009/07/30 13:36:50 :: Failed to find status in wpa_cli result 
2009/07/30 13:36:50 :: exiting connection thread
2009/07/30 13:36:53 :: No wired connection present, attempting to autoconnect to wireless network
2009/07/30 13:36:53 :: trying to automatically connect to...***
2009/07/30 13:36:53 :: Connecting to wireless network ***
2009/07/30 13:36:53 :: Putting interface down
2009/07/30 13:36:53 :: Releasing DHCP leases...
2009/07/30 13:36:54 :: Setting false IP...
2009/07/30 13:36:54 :: Stopping wpa_supplicant and any DHCP clients
2009/07/30 13:36:54 :: Flushing the routing table...
2009/07/30 13:36:54 :: Generating psk...
2009/07/30 13:36:54 :: WARNING: PSK generation failed!  Falling back to wireless key.
2009/07/30 13:36:54 :: Please report this error to the wicd developers!
2009/07/30 13:36:54 :: Attempting to authenticate...
2009/07/30 13:36:54 :: Putting interface up...
2009/07/30 13:36:54 :: Failed to find status in wpa_cli result 
2009/07/30 13:36:54 :: exiting connection thread
2009/07/30 13:36:57 :: No wired connection present, attempting to autoconnect to wireless network
2009/07/30 13:36:57 :: trying to automatically connect to...***
2009/07/30 13:36:57 :: Connecting to wireless network ***
2009/07/30 13:36:57 :: Putting interface down
2009/07/30 13:36:57 :: Releasing DHCP leases...
2009/07/30 13:36:57 :: Setting false IP...
2009/07/30 13:36:57 :: Stopping wpa_supplicant and any DHCP clients
2009/07/30 13:36:57 :: Flushing the routing table...
2009/07/30 13:36:57 :: Generating psk...
2009/07/30 13:36:57 :: WARNING: PSK generation failed!  Falling back to wireless key.
2009/07/30 13:36:57 :: Please report this error to the wicd developers!
2009/07/30 13:36:57 :: Attempting to authenticate...
2009/07/30 13:36:57 :: Putting interface up...
2009/07/30 13:36:58 :: Failed to find status in wpa_cli result 
2009/07/30 13:36:58 :: exiting connection thread
2009/07/30 13:40:55 :: Connecting to wireless network ***
2009/07/30 13:40:55 :: Putting interface down
2009/07/30 13:40:55 :: Releasing DHCP leases...
2009/07/30 13:40:55 :: Setting false IP...
2009/07/30 13:40:55 :: Stopping wpa_supplicant and any DHCP clients
2009/07/30 13:40:55 :: Flushing the routing table...
2009/07/30 13:40:55 :: Attempting to authenticate...
2009/07/30 13:40:55 :: Putting interface up...
2009/07/30 13:40:55 :: Failed to find status in wpa_cli result 
2009/07/30 13:40:55 :: exiting connection thread
2009/07/30 13:41:57 :: No wired connection present, attempting to autoconnect to wireless network
2009/07/30 13:41:57 :: trying to automatically connect to...***
2009/07/30 13:41:57 :: Connecting to wireless network ***
2009/07/30 13:41:57 :: Putting interface down
2009/07/30 13:41:57 :: Releasing DHCP leases...
2009/07/30 13:41:57 :: Setting false IP...
2009/07/30 13:41:57 :: Stopping wpa_supplicant and any DHCP clients
2009/07/30 13:41:57 :: Flushing the routing table...
2009/07/30 13:41:57 :: Generating psk...
2009/07/30 13:41:57 :: WARNING: PSK generation failed!  Falling back to wireless key.
2009/07/30 13:41:57 :: Please report this error to the wicd developers!
2009/07/30 13:41:57 :: Attempting to authenticate...
2009/07/30 13:41:57 :: Putting interface up...
2009/07/30 13:41:57 :: Failed to find status in wpa_cli result 
2009/07/30 13:41:57 :: exiting connection thread

```

wpa_supplicant.conf:

```

eapol_version=1
fast_reauth=1
network={
	ssid="***"
	scan_ssid=1
	key_mgmt=WPA-EAP
	eap=TTLS
	identity="***"
	password="***"
	phase2="auth=PAP"
}

```

```

name = PEAP with TKIP
author = Fralaltro
version = 1
require identity *Identity password *Password 
-----
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="$_ESSID"
        scan_ssid=$_SCAN
        proto=WPA
        key_mgmt=WPA-EAP
        pairwise=TKIP
        group=TKIP
        eap=PEAP
        identity="$_IDENTITY"
        password="$_PASSWORD"
        phase1="peaplabel=0"
        phase2="auth=MSCHAPV2"
}

```

I'm not sure where to go next in debugging... help!

---

