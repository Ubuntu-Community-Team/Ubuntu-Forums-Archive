---
title: "New wireless issue, Inspiron 5100"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by mlthmp on 2010-04-12
This morning when I turned my my Inspiron 5100 I get a new message on the screen. Wireless has been working up till this morning, but now nothing =(

"Wicd needs to access your computer's network cards" Then it asks for a PW. So I enter my password in.

"Could not connect to wicd's D-Bus interface. Check the wicd log for error message"

When I hit OK, I get the disconnected bubble on the bottom of the screen, and another popup that reads "The wicd daemon has shut down. The UI will not function properly until it is restarted"

I have searched for the wicd.log file, but haven't been able to locate it yet.

The only way I am able to access the internet right now is to reboot, and hookup via ethernet. 

Any suggestions? 

Using Ubuntu Alt install command line, with lubuntu-desktop installed.

---

### Post by chili555 on 2010-04-12
> I have searched for the wicd.log file, but haven't been able to locate it yet.It's in /var/log/wicd/wicd.log. What does it say?

---

### Post by mlthmp on 2010-04-13
> **chili555 said:**
> It's in /var/log/wicd/wicd.log. What does it say?


Ahh! ok, thanks!

Here is the contents, I appreciate the assistance =)

2010/04/10 06:17:13 :: ---------------------------
2010/04/10 06:17:13 :: wicd initializing...
2010/04/10 06:17:13 :: ---------------------------
2010/04/10 06:17:13 :: wicd is version 1.6.1 426
2010/04/10 06:17:13 :: did not find backend in configuration, setting default external
2010/04/10 06:17:13 :: setting backend to external
2010/04/10 06:17:13 :: trying to load backend external
2010/04/10 06:17:13 :: successfully loaded backend external
2010/04/10 06:17:13 :: trying to load backend external
2010/04/10 06:17:13 :: successfully loaded backend external
2010/04/10 06:17:13 :: Automatically detected wireless interface wlan0
2010/04/10 06:17:13 :: did not find wireless_interface in configuration, setting default wlan0
2010/04/10 06:17:13 :: setting wireless interface wlan0
2010/04/10 06:17:13 :: automatically detected wired interface eth0
2010/04/10 06:17:13 :: did not find wired_interface in configuration, setting default eth0
2010/04/10 06:17:13 :: setting wired interface eth0
2010/04/10 06:17:13 :: did not find wpa_driver in configuration, setting default wext
2010/04/10 06:17:13 :: setting wpa driver wext
2010/04/10 06:17:13 :: did not find always_show_wired_interface in configuration, setting default False
2010/04/10 06:17:13 :: did not find use_global_dns in configuration, setting default False
2010/04/10 06:17:13 :: setting use global dns to False
2010/04/10 06:17:13 :: did not find global_dns_1 in configuration, setting default None
2010/04/10 06:17:13 :: did not find global_dns_2 in configuration, setting default None
2010/04/10 06:17:13 :: did not find global_dns_3 in configuration, setting default None
2010/04/10 06:17:13 :: did not find global_dns_dom in configuration, setting default None
2010/04/10 06:17:13 :: did not find global_search_dom in configuration, setting default None
2010/04/10 06:17:13 :: setting global dns
2010/04/10 06:17:13 :: global dns servers are None None None
2010/04/10 06:17:13 :: domain is None
2010/04/10 06:17:13 :: search domain is None
2010/04/10 06:17:13 :: did not find auto_reconnect in configuration, setting default True
2010/04/10 06:17:13 :: setting automatically reconnect when connection drops True
2010/04/10 06:17:13 :: did not find debug_mode in configuration, setting default False
2010/04/10 06:17:13 :: did not find wired_connect_mode in configuration, setting default 1
2010/04/10 06:17:13 :: did not find signal_display_type in configuration, setting default 0
2010/04/10 06:17:13 :: did not find dhcp_client in configuration, setting default 0
2010/04/10 06:17:13 :: Setting dhcp client to 0
2010/04/10 06:17:13 :: did not find link_detect_tool in configuration, setting default 0
2010/04/10 06:17:13 :: did not find flush_tool in configuration, setting default 0
2010/04/10 06:17:13 :: did not find sudo_app in configuration, setting default 0
2010/04/10 06:17:13 :: did not find prefer_wired in configuration, setting default False
2010/04/10 06:17:13 :: Wireless configuration file not found, creating...
2010/04/10 06:17:13 :: Wired configuration file not found, creating a default...
2010/04/10 06:17:13 :: Creating wired profile for wired-default
2010/04/10 06:17:13 :: chmoding configuration files 0600...
2010/04/10 06:17:13 :: chowning configuration files root:root...
2010/04/10 06:17:13 :: Using wireless interface...wlan0
2010/04/10 06:17:13 :: Using wired interface...eth0
2010/04/10 06:19:16 :: ---------------------------
2010/04/10 06:19:16 :: wicd initializing...
2010/04/10 06:19:16 :: ---------------------------
2010/04/10 06:19:16 :: wicd is version 1.6.1 426
2010/04/10 06:19:16 :: setting backend to external
2010/04/10 06:19:16 :: trying to load backend external
2010/04/10 06:19:17 :: successfully loaded backend external
2010/04/10 06:19:17 :: trying to load backend external
2010/04/10 06:19:17 :: successfully loaded backend external
2010/04/10 06:19:17 :: Automatically detected wireless interface wlan0
2010/04/10 06:19:17 :: setting wireless interface wlan0
2010/04/10 06:19:17 :: automatically detected wired interface eth0
2010/04/10 06:19:17 :: setting wired interface eth0
2010/04/10 06:19:17 :: setting wpa driver wext
2010/04/10 06:19:17 :: setting use global dns to False
2010/04/10 06:19:17 :: setting global dns
2010/04/10 06:19:17 :: global dns servers are None None None
2010/04/10 06:19:17 :: domain is None
2010/04/10 06:19:17 :: search domain is None
2010/04/10 06:19:17 :: setting automatically reconnect when connection drops True
2010/04/10 06:19:17 :: Setting dhcp client to 0
2010/04/10 06:19:17 :: Wireless configuration file found...
2010/04/10 06:19:17 :: Wired configuration file found...
2010/04/10 06:19:17 :: chmoding configuration files 0600...
2010/04/10 06:19:17 :: chowning configuration files root:root...
2010/04/10 06:19:17 :: Using wireless interface...wlan0
2010/04/10 06:19:17 :: Using wired interface...eth0
2010/04/10 06:35:26 :: ---------------------------
2010/04/10 06:35:26 :: wicd initializing...
2010/04/10 06:35:26 :: ---------------------------
2010/04/10 06:35:26 :: wicd is version 1.6.1 426
2010/04/10 06:35:26 :: setting backend to external
2010/04/10 06:35:26 :: trying to load backend external
2010/04/10 06:35:27 :: successfully loaded backend external
2010/04/10 06:35:27 :: trying to load backend external
2010/04/10 06:35:27 :: successfully loaded backend external
2010/04/10 06:35:27 :: Automatically detected wireless interface wlan0
2010/04/10 06:35:27 :: setting wireless interface wlan0
2010/04/10 06:35:27 :: automatically detected wired interface eth0
2010/04/10 06:35:27 :: setting wired interface eth0
2010/04/10 06:35:27 :: setting wpa driver wext
2010/04/10 06:35:27 :: setting use global dns to False
2010/04/10 06:35:27 :: setting global dns
2010/04/10 06:35:27 :: global dns servers are None None None
2010/04/10 06:35:27 :: domain is None
2010/04/10 06:35:27 :: search domain is None
2010/04/10 06:35:27 :: setting automatically reconnect when connection drops True
2010/04/10 06:35:28 :: Setting dhcp client to 0
2010/04/10 06:35:29 :: Wireless configuration file found...
2010/04/10 06:35:29 :: Wired configuration file found...
2010/04/10 06:35:29 :: chmoding configuration files 0600...
2010/04/10 06:35:29 :: chowning configuration files root:root...
2010/04/10 06:35:29 :: Using wireless interface...wlan0
2010/04/10 06:35:29 :: Using wired interface...eth0
2010/04/10 06:42:35 :: did not find window_width in configuration, setting default -1
2010/04/10 06:42:35 :: did not find window_height in configuration, setting default -1
2010/04/10 06:42:50 :: did not find pref_width in configuration, setting default -1
2010/04/10 06:42:50 :: did not find pref_height in configuration, setting default -1
2010/04/10 06:42:51 :: trying to load backend ioctl
2010/04/10 06:42:51 :: WARNING: python-iwscan not found, falling back to using iwlist scan.
2010/04/10 06:42:51 :: WARNING: python-wpactrl not found, falling back to using wpa_cli.
2010/04/10 06:42:51 :: trying to load backend external
2010/04/10 06:43:27 :: Putting interface down
2010/04/10 06:43:27 :: Releasing DHCP leases...
2010/04/10 06:43:27 :: Setting false IP...
2010/04/10 06:43:27 :: Flushing the routing table...
2010/04/10 06:43:27 :: Putting interface up...
2010/04/10 06:43:27 :: Running DHCP
2010/04/10 06:43:27 :: Internet Systems Consortium DHCP Client V3.1.2
2010/04/10 06:43:27 :: Copyright 2004-2008 Internet Systems Consortium.
2010/04/10 06:43:27 :: All rights reserved.
2010/04/10 06:43:27 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/04/10 06:43:27 :: 
2010/04/10 06:43:28 :: Listening on LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 06:43:28 :: Sending on   LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 06:43:28 :: Sending on   Socket/fallback
2010/04/10 06:43:30 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
2010/04/10 06:43:33 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
2010/04/10 06:43:39 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
2010/04/10 06:43:46 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
2010/04/10 06:43:47 :: receive_packet failed on eth0: Network is down
2010/04/10 06:43:56 :: canceling connection attempt
2010/04/10 06:43:56 :: running kill dhcp.
2010/04/10 06:43:56 :: DHCP connection failed
2010/04/10 06:43:56 :: exiting connection thread
2010/04/10 06:43:57 :: Sending connection attempt result aborted
2010/04/10 06:48:58 :: Daemon going down, killing wicd-monitor...
2010/04/10 06:48:58 :: Removing PID file...
2010/04/10 06:48:58 :: Shutting down...
2010/04/10 06:52:32 :: ---------------------------
2010/04/10 06:52:32 :: wicd initializing...
2010/04/10 06:52:32 :: ---------------------------
2010/04/10 06:52:32 :: wicd is version 1.6.1 426
2010/04/10 06:52:32 :: setting backend to external
2010/04/10 06:52:32 :: trying to load backend external
2010/04/10 06:52:32 :: successfully loaded backend external
2010/04/10 06:52:32 :: trying to load backend external
2010/04/10 06:52:32 :: successfully loaded backend external
2010/04/10 06:52:32 :: Automatically detected wireless interface wlan0
2010/04/10 06:52:32 :: setting wireless interface wlan0
2010/04/10 06:52:32 :: automatically detected wired interface eth0
2010/04/10 06:52:32 :: setting wired interface eth0
2010/04/10 06:52:32 :: setting wpa driver wext
2010/04/10 06:52:32 :: setting use global dns to False
2010/04/10 06:52:32 :: setting global dns
2010/04/10 06:52:32 :: global dns servers are None None None
2010/04/10 06:52:32 :: domain is None
2010/04/10 06:52:32 :: search domain is None
2010/04/10 06:52:32 :: setting automatically reconnect when connection drops True
2010/04/10 06:52:33 :: Setting dhcp client to 0
2010/04/10 06:52:33 :: Wireless configuration file found...
2010/04/10 06:52:33 :: Wired configuration file found...
2010/04/10 06:52:33 :: chmoding configuration files 0600...
2010/04/10 06:52:33 :: chowning configuration files root:root...
2010/04/10 06:52:33 :: Using wireless interface...wlan0
2010/04/10 06:52:33 :: Using wired interface...eth0
2010/04/10 06:52:40 :: Autoconnecting...
2010/04/10 06:52:40 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:52:40 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:52:45 :: Autoconnecting...
2010/04/10 06:52:45 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:52:45 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:52:50 :: Autoconnecting...
2010/04/10 06:52:50 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:52:50 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:52:55 :: Autoconnecting...
2010/04/10 06:52:55 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:52:55 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:54:58 :: Daemon going down, killing wicd-monitor...
2010/04/10 06:54:58 :: Removing PID file...
2010/04/10 06:54:58 :: Shutting down...
2010/04/10 06:56:14 :: ---------------------------
2010/04/10 06:56:14 :: wicd initializing...
2010/04/10 06:56:14 :: ---------------------------
2010/04/10 06:56:14 :: wicd is version 1.6.1 426
2010/04/10 06:56:14 :: setting backend to external
2010/04/10 06:56:14 :: trying to load backend external
2010/04/10 06:56:14 :: successfully loaded backend external
2010/04/10 06:56:14 :: trying to load backend external
2010/04/10 06:56:14 :: successfully loaded backend external
2010/04/10 06:56:15 :: Automatically detected wireless interface wlan0
2010/04/10 06:56:15 :: setting wireless interface wlan0
2010/04/10 06:56:15 :: automatically detected wired interface eth0
2010/04/10 06:56:15 :: setting wired interface eth0
2010/04/10 06:56:15 :: setting wpa driver wext
2010/04/10 06:56:15 :: setting use global dns to False
2010/04/10 06:56:15 :: setting global dns
2010/04/10 06:56:15 :: global dns servers are None None None
2010/04/10 06:56:15 :: domain is None
2010/04/10 06:56:15 :: search domain is None
2010/04/10 06:56:15 :: setting automatically reconnect when connection drops True
2010/04/10 06:56:16 :: Setting dhcp client to 0
2010/04/10 06:56:16 :: Wireless configuration file found...
2010/04/10 06:56:16 :: Wired configuration file found...
2010/04/10 06:56:16 :: chmoding configuration files 0600...
2010/04/10 06:56:16 :: chowning configuration files root:root...
2010/04/10 06:56:16 :: Using wireless interface...wlan0
2010/04/10 06:56:16 :: Using wired interface...eth0
2010/04/10 06:56:22 :: Autoconnecting...
2010/04/10 06:56:22 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:56:22 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:56:27 :: Autoconnecting...
2010/04/10 06:56:27 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:56:27 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:56:32 :: Autoconnecting...
2010/04/10 06:56:32 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:56:32 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 06:56:37 :: Autoconnecting...
2010/04/10 06:56:37 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 06:56:37 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 07:01:31 :: ---------------------------
2010/04/10 07:01:31 :: wicd initializing...
2010/04/10 07:01:31 :: ---------------------------
2010/04/10 07:01:31 :: wicd is version 1.6.1 426
2010/04/10 07:01:31 :: setting backend to external
2010/04/10 07:01:31 :: trying to load backend external
2010/04/10 07:01:32 :: successfully loaded backend external
2010/04/10 07:01:32 :: trying to load backend external
2010/04/10 07:01:32 :: successfully loaded backend external
2010/04/10 07:01:32 :: Automatically detected wireless interface wlan0
2010/04/10 07:01:32 :: setting wireless interface wlan0
2010/04/10 07:01:32 :: automatically detected wired interface eth0
2010/04/10 07:01:32 :: setting wired interface eth0
2010/04/10 07:01:32 :: setting wpa driver wext
2010/04/10 07:01:32 :: setting use global dns to False
2010/04/10 07:01:32 :: setting global dns
2010/04/10 07:01:32 :: global dns servers are None None None
2010/04/10 07:01:32 :: domain is None
2010/04/10 07:01:32 :: search domain is None
2010/04/10 07:01:32 :: setting automatically reconnect when connection drops True
2010/04/10 07:01:33 :: Setting dhcp client to 0
2010/04/10 07:01:33 :: Wireless configuration file found...
2010/04/10 07:01:33 :: Wired configuration file found...
2010/04/10 07:01:33 :: chmoding configuration files 0600...
2010/04/10 07:01:33 :: chowning configuration files root:root...
2010/04/10 07:01:33 :: Using wireless interface...wlan0
2010/04/10 07:01:33 :: Using wired interface...eth0
2010/04/10 07:01:40 :: Autoconnecting...
2010/04/10 07:01:40 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 07:01:40 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 07:01:45 :: Autoconnecting...
2010/04/10 07:01:45 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 07:01:45 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 07:01:50 :: Autoconnecting...
2010/04/10 07:01:50 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 07:01:50 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 07:01:55 :: Autoconnecting...
2010/04/10 07:01:55 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 07:01:55 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 07:02:43 :: trying to load backend ioctl
2010/04/10 07:02:43 :: WARNING: python-iwscan not found, falling back to using iwlist scan.
2010/04/10 07:02:43 :: WARNING: python-wpactrl not found, falling back to using wpa_cli.
2010/04/10 07:02:43 :: trying to load backend external
2010/04/10 12:45:27 :: ---------------------------
2010/04/10 12:45:27 :: wicd initializing...
2010/04/10 12:45:27 :: ---------------------------
2010/04/10 12:45:27 :: wicd is version 1.6.1 426
2010/04/10 12:45:27 :: setting backend to external
2010/04/10 12:45:27 :: trying to load backend external
2010/04/10 12:45:27 :: successfully loaded backend external
2010/04/10 12:45:27 :: trying to load backend external
2010/04/10 12:45:27 :: successfully loaded backend external
2010/04/10 12:45:27 :: Automatically detected wireless interface wlan0
2010/04/10 12:45:27 :: setting wireless interface wlan0
2010/04/10 12:45:27 :: automatically detected wired interface eth0
2010/04/10 12:45:27 :: setting wired interface eth0
2010/04/10 12:45:27 :: setting wpa driver wext
2010/04/10 12:45:28 :: setting use global dns to False
2010/04/10 12:45:28 :: setting global dns
2010/04/10 12:45:28 :: global dns servers are None None None
2010/04/10 12:45:28 :: domain is None
2010/04/10 12:45:28 :: search domain is None
2010/04/10 12:45:28 :: setting automatically reconnect when connection drops True
2010/04/10 12:45:29 :: Setting dhcp client to 0
2010/04/10 12:45:29 :: Wireless configuration file found...
2010/04/10 12:45:29 :: Wired configuration file found...
2010/04/10 12:45:29 :: chmoding configuration files 0600...
2010/04/10 12:45:29 :: chowning configuration files root:root...
2010/04/10 12:45:29 :: Using wireless interface...wlan0
2010/04/10 12:45:29 :: Using wired interface...eth0
2010/04/10 12:45:36 :: Autoconnecting...
2010/04/10 12:45:36 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 12:45:36 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 12:45:41 :: Autoconnecting...
2010/04/10 12:45:41 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 12:45:41 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 12:45:46 :: Autoconnecting...
2010/04/10 12:45:46 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 12:45:46 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 12:45:51 :: Autoconnecting...
2010/04/10 12:45:51 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 12:45:51 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 12:49:16 :: Autoconnecting...
2010/04/10 12:49:16 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 12:49:16 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 12:52:41 :: Autoconnecting...
2010/04/10 12:52:41 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 12:52:41 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 12:55:19 :: Putting interface down
2010/04/10 12:55:19 :: Releasing DHCP leases...
2010/04/10 12:55:19 :: Setting false IP...
2010/04/10 12:55:19 :: Flushing the routing table...
2010/04/10 12:55:19 :: Putting interface up...
2010/04/10 12:55:19 :: Running DHCP
2010/04/10 12:55:19 :: Internet Systems Consortium DHCP Client V3.1.2
2010/04/10 12:55:19 :: Copyright 2004-2008 Internet Systems Consortium.
2010/04/10 12:55:19 :: All rights reserved.
2010/04/10 12:55:19 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/04/10 12:55:19 :: 
2010/04/10 12:55:20 :: Listening on LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 12:55:20 :: Sending on   LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 12:55:20 :: Sending on   Socket/fallback
2010/04/10 12:55:24 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
2010/04/10 12:55:24 :: DHCPOFFER of 192.168.1.100 from 192.168.1.1
2010/04/10 12:55:25 :: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
2010/04/10 12:55:25 :: DHCPACK of 192.168.1.100 from 192.168.1.1
2010/04/10 12:55:25 :: bound to 192.168.1.100 -- renewal in 35698 seconds.
2010/04/10 12:55:25 :: DHCP connection successful
2010/04/10 12:55:25 :: Connecting thread exiting.
2010/04/10 12:55:25 :: Sending connection attempt result Success
2010/04/10 14:24:47 :: ---------------------------
2010/04/10 14:24:47 :: wicd initializing...
2010/04/10 14:24:47 :: ---------------------------
2010/04/10 14:24:47 :: wicd is version 1.6.1 426
2010/04/10 14:24:47 :: setting backend to external
2010/04/10 14:24:47 :: trying to load backend external
2010/04/10 14:24:48 :: successfully loaded backend external
2010/04/10 14:24:48 :: trying to load backend external
2010/04/10 14:24:48 :: successfully loaded backend external
2010/04/10 14:24:48 :: Automatically detected wireless interface wlan0
2010/04/10 14:24:48 :: setting wireless interface wlan0
2010/04/10 14:24:48 :: automatically detected wired interface eth0
2010/04/10 14:24:48 :: setting wired interface eth0
2010/04/10 14:24:48 :: setting wpa driver wext
2010/04/10 14:24:48 :: setting use global dns to False
2010/04/10 14:24:48 :: setting global dns
2010/04/10 14:24:48 :: global dns servers are None None None
2010/04/10 14:24:48 :: domain is None
2010/04/10 14:24:48 :: search domain is None
2010/04/10 14:24:48 :: setting automatically reconnect when connection drops True
2010/04/10 14:24:48 :: Setting dhcp client to 0
2010/04/10 14:24:49 :: Wireless configuration file found...
2010/04/10 14:24:49 :: Wired configuration file found...
2010/04/10 14:24:49 :: chmoding configuration files 0600...
2010/04/10 14:24:49 :: chowning configuration files root:root...
2010/04/10 14:24:49 :: Using wireless interface...wlan0
2010/04/10 14:24:49 :: Using wired interface...eth0
2010/04/10 14:24:55 :: Autoconnecting...
2010/04/10 14:24:55 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:24:55 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:25:00 :: Autoconnecting...
2010/04/10 14:25:00 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:25:00 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:25:05 :: Autoconnecting...
2010/04/10 14:25:05 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:25:05 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:25:10 :: Autoconnecting...
2010/04/10 14:25:10 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:25:10 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:27:16 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:16 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:16 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:16 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:16 :: Putting interface down
2010/04/10 14:27:16 :: Releasing DHCP leases...
2010/04/10 14:27:16 :: Setting false IP...
2010/04/10 14:27:16 :: Flushing the routing table...
2010/04/10 14:27:16 :: Putting interface up...
2010/04/10 14:27:16 :: Running DHCP
2010/04/10 14:27:16 :: Internet Systems Consortium DHCP Client V3.1.2
2010/04/10 14:27:16 :: Copyright 2004-2008 Internet Systems Consortium.
2010/04/10 14:27:16 :: All rights reserved.
2010/04/10 14:27:16 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/04/10 14:27:16 :: 
2010/04/10 14:27:17 :: Listening on LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 14:27:17 :: Sending on   LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 14:27:17 :: Sending on   Socket/fallback
2010/04/10 14:27:21 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
2010/04/10 14:27:22 :: DHCPOFFER of 192.168.1.100 from 192.168.1.1
2010/04/10 14:27:22 :: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
2010/04/10 14:27:22 :: DHCPACK of 192.168.1.100 from 192.168.1.1
2010/04/10 14:27:22 :: bound to 192.168.1.100 -- renewal in 35524 seconds.
2010/04/10 14:27:22 :: DHCP connection successful
2010/04/10 14:27:22 :: Connecting thread exiting.
2010/04/10 14:27:27 :: Sending connection attempt result Success
2010/04/10 14:27:27 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:27 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:27 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:27 :: GetWiredProperty: WiredNetwork does not exist
2010/04/10 14:27:28 :: Putting interface down
2010/04/10 14:27:28 :: Releasing DHCP leases...
2010/04/10 14:27:28 :: Setting false IP...
2010/04/10 14:27:28 :: Flushing the routing table...
2010/04/10 14:27:28 :: Putting interface up...
2010/04/10 14:27:28 :: Running DHCP
2010/04/10 14:27:28 :: Internet Systems Consortium DHCP Client V3.1.2
2010/04/10 14:27:28 :: Copyright 2004-2008 Internet Systems Consortium.
2010/04/10 14:27:28 :: All rights reserved.
2010/04/10 14:27:28 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/04/10 14:27:28 :: 
2010/04/10 14:27:29 :: Listening on LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 14:27:29 :: Sending on   LPF/eth0/00:0d:56:36:c2:fe
2010/04/10 14:27:29 :: Sending on   Socket/fallback
2010/04/10 14:27:33 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
2010/04/10 14:27:34 :: DHCPOFFER of 192.168.1.100 from 192.168.1.1
2010/04/10 14:27:34 :: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
2010/04/10 14:27:34 :: DHCPACK of 192.168.1.100 from 192.168.1.1
2010/04/10 14:27:34 :: bound to 192.168.1.100 -- renewal in 41493 seconds.
2010/04/10 14:27:34 :: DHCP connection successful
2010/04/10 14:27:34 :: Connecting thread exiting.
2010/04/10 14:27:34 :: Sending connection attempt result Success
2010/04/10 14:29:32 :: Autoconnecting...
2010/04/10 14:29:32 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:29:33 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:29:33 :: Autoconnecting...
2010/04/10 14:29:33 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:29:35 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:29:40 :: Autoconnecting...
2010/04/10 14:29:40 :: No wired connection present, attempting to autoconnect to wireless network
2010/04/10 14:29:41 :: Unable to autoconnect, you'll have to manually connect
2010/04/10 14:29:42 :: Connecting to wireless network linksys
2010/04/10 14:29:43 :: Putting interface down
2010/04/10 14:29:43 :: Releasing DHCP leases...
2010/04/10 14:29:43 :: Setting false IP...
2010/04/10 14:29:43 :: Stopping wpa_supplicant
2010/04/10 14:29:43 :: Flushing the routing table...
2010/04/10 14:29:43 :: Putting interface up...
2010/04/10 14:29:43 :: Running DHCP
2010/04/10 14:29:43 :: Internet Systems Consortium DHCP Client V3.1.2
2010/04/10 14:29:43 :: Copyright 2004-2008 Internet Systems Consortium.
2010/04/10 14:29:43 :: All rights reserved.
2010/04/10 14:29:43 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/04/10 14:29:43 :: 
2010/04/10 14:29:44 :: Listening on LPF/wlan0/00:90:4b:12:a1:13
2010/04/10 14:29:44 :: Sending on   LPF/wlan0/00:90:4b:12:a1:13
2010/04/10 14:29:44 :: Sending on   Socket/fallback
2010/04/10 14:29:48 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
2010/04/10 14:29:49 :: DHCPOFFER of 192.168.1.106 from 192.168.1.1
2010/04/10 14:29:49 :: DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
2010/04/10 14:29:49 :: DHCPACK of 192.168.1.106 from 192.168.1.1
2010/04/10 14:29:49 :: bound to 192.168.1.106 -- renewal in 40103 seconds.
2010/04/10 14:29:49 :: DHCP connection successful
2010/04/10 14:29:49 :: Connecting thread exiting.
2010/04/10 14:29:54 :: Sending connection attempt result Success
2010/04/10 14:33:29 :: Daemon going down, killing wicd-monitor...
2010/04/10 14:33:29 :: Removing PID file...
2010/04/10 14:33:29 :: Shutting down...
2010/04/12 03:54:29 :: ---------------------------
2010/04/12 03:54:29 :: wicd initializing...
2010/04/12 03:54:29 :: ---------------------------
2010/04/12 03:54:29 :: wicd is version 1.6.1 426
2010/04/12 03:54:29 :: Traceback (most recent call last):
2010/04/12 03:54:29 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 03:54:29 ::     main(sys.argv)
2010/04/12 03:54:29 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 03:54:29 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 03:54:29 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 03:54:29 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 03:54:29 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 03:54:29 ::     debug=debug)
2010/04/12 03:54:29 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 03:54:29 ::     self.read(path)
2010/04/12 03:54:29 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 03:54:29 ::     self._read(fp, filename)
2010/04/12 03:54:29 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 03:54:29 ::     raise e
2010/04/12 03:54:29 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 03:54:29 ::     [line 23]: '[]\n'
2010/04/12 03:56:10 :: ---------------------------
2010/04/12 03:56:10 :: wicd initializing...
2010/04/12 03:56:10 :: ---------------------------
2010/04/12 03:56:10 :: wicd is version 1.6.1 426
2010/04/12 03:56:10 :: Traceback (most recent call last):
2010/04/12 03:56:10 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 03:56:10 ::     main(sys.argv)
2010/04/12 03:56:10 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 03:56:10 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 03:56:10 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 03:56:10 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 03:56:10 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 03:56:10 ::     debug=debug)
2010/04/12 03:56:10 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 03:56:10 ::     self.read(path)
2010/04/12 03:56:10 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 03:56:10 ::     self._read(fp, filename)
2010/04/12 03:56:10 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 03:56:10 ::     raise e
2010/04/12 03:56:10 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 03:56:10 ::     [line 23]: '[]\n'
2010/04/12 03:56:40 :: ---------------------------
2010/04/12 03:56:40 :: wicd initializing...
2010/04/12 03:56:40 :: ---------------------------
2010/04/12 03:56:40 :: wicd is version 1.6.1 426
2010/04/12 03:56:40 :: Traceback (most recent call last):
2010/04/12 03:56:40 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 03:56:40 ::     main(sys.argv)
2010/04/12 03:56:40 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 03:56:40 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 03:56:40 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 03:56:40 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 03:56:40 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 03:56:40 ::     debug=debug)
2010/04/12 03:56:40 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 03:56:40 ::     self.read(path)
2010/04/12 03:56:40 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 03:56:40 ::     self._read(fp, filename)
2010/04/12 03:56:40 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 03:56:40 ::     raise e
2010/04/12 03:56:40 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 03:56:40 ::     [line 23]: '[]\n'
2010/04/12 01:58:55 :: ---------------------------
2010/04/12 01:58:55 :: wicd initializing...
2010/04/12 01:58:55 :: ---------------------------
2010/04/12 01:58:55 :: wicd is version 1.6.1 426
2010/04/12 01:58:55 :: Traceback (most recent call last):
2010/04/12 01:58:55 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 01:58:55 ::     main(sys.argv)
2010/04/12 01:58:55 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 01:58:55 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 01:58:55 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 01:58:55 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 01:58:55 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 01:58:55 ::     debug=debug)
2010/04/12 01:58:55 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 01:58:55 ::     self.read(path)
2010/04/12 01:58:55 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 01:58:55 ::     self._read(fp, filename)
2010/04/12 01:58:55 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 01:58:55 ::     raise e
2010/04/12 01:58:55 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 01:58:55 ::     [line 23]: '[]\n'
2010/04/12 01:59:35 :: ---------------------------
2010/04/12 01:59:35 :: wicd initializing...
2010/04/12 01:59:35 :: ---------------------------
2010/04/12 01:59:35 :: wicd is version 1.6.1 426
2010/04/12 01:59:35 :: Traceback (most recent call last):
2010/04/12 01:59:35 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 01:59:35 ::     main(sys.argv)
2010/04/12 01:59:35 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 01:59:35 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 01:59:35 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 01:59:35 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 01:59:35 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 01:59:35 ::     debug=debug)
2010/04/12 01:59:35 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 01:59:35 ::     self.read(path)
2010/04/12 01:59:35 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 01:59:35 ::     self._read(fp, filename)
2010/04/12 01:59:35 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 01:59:35 ::     raise e
2010/04/12 01:59:35 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 01:59:35 ::     [line 23]: '[]\n'
2010/04/12 02:07:03 :: ---------------------------
2010/04/12 02:07:03 :: wicd initializing...
2010/04/12 02:07:03 :: ---------------------------
2010/04/12 02:07:03 :: wicd is version 1.6.1 426
2010/04/12 02:07:03 :: Traceback (most recent call last):
2010/04/12 02:07:03 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 02:07:03 ::     main(sys.argv)
2010/04/12 02:07:03 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 02:07:03 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 02:07:03 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 02:07:03 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 02:07:03 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 02:07:03 ::     debug=debug)
2010/04/12 02:07:03 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 02:07:03 ::     self.read(path)
2010/04/12 02:07:03 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 02:07:03 ::     self._read(fp, filename)
2010/04/12 02:07:03 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 02:07:03 ::     raise e
2010/04/12 02:07:03 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 02:07:03 ::     [line 23]: '[]\n'
2010/04/12 02:07:50 :: ---------------------------
2010/04/12 02:07:51 :: wicd initializing...
2010/04/12 02:07:51 :: ---------------------------
2010/04/12 02:07:51 :: wicd is version 1.6.1 426
2010/04/12 02:07:51 :: Traceback (most recent call last):
2010/04/12 02:07:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 02:07:51 ::     main(sys.argv)
2010/04/12 02:07:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 02:07:51 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 02:07:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 02:07:51 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 02:07:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 02:07:51 ::     debug=debug)
2010/04/12 02:07:51 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 02:07:51 ::     self.read(path)
2010/04/12 02:07:51 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 02:07:51 ::     self._read(fp, filename)
2010/04/12 02:07:51 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 02:07:51 ::     raise e
2010/04/12 02:07:51 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 02:07:51 ::     [line 23]: '[]\n'
2010/04/12 04:09:25 :: ---------------------------
2010/04/12 04:09:25 :: wicd initializing...
2010/04/12 04:09:25 :: ---------------------------
2010/04/12 04:09:25 :: wicd is version 1.6.1 426
2010/04/12 04:09:26 :: Traceback (most recent call last):
2010/04/12 04:09:26 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:09:26 ::     main(sys.argv)
2010/04/12 04:09:26 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:09:26 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:09:26 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:09:26 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:09:26 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:09:26 ::     debug=debug)
2010/04/12 04:09:26 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:09:26 ::     self.read(path)
2010/04/12 04:09:26 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:09:26 ::     self._read(fp, filename)
2010/04/12 04:09:26 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:09:26 ::     raise e
2010/04/12 04:09:26 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:09:26 ::     [line 23]: '[]\n'
2010/04/12 04:10:19 :: ---------------------------
2010/04/12 04:10:19 :: wicd initializing...
2010/04/12 04:10:19 :: ---------------------------
2010/04/12 04:10:19 :: wicd is version 1.6.1 426
2010/04/12 04:10:19 :: Traceback (most recent call last):
2010/04/12 04:10:19 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:10:19 ::     main(sys.argv)
2010/04/12 04:10:19 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:10:19 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:10:19 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:10:19 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:10:19 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:10:19 ::     debug=debug)
2010/04/12 04:10:19 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:10:19 ::     self.read(path)
2010/04/12 04:10:19 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:10:19 ::     self._read(fp, filename)
2010/04/12 04:10:19 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:10:19 ::     raise e
2010/04/12 04:10:19 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:10:19 ::     [line 23]: '[]\n'
2010/04/12 04:11:32 :: ---------------------------
2010/04/12 04:11:32 :: wicd initializing...
2010/04/12 04:11:32 :: ---------------------------
2010/04/12 04:11:32 :: wicd is version 1.6.1 426
2010/04/12 04:11:32 :: Traceback (most recent call last):
2010/04/12 04:11:32 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:11:32 ::     main(sys.argv)
2010/04/12 04:11:32 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:11:32 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:11:32 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:11:32 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:11:32 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:11:32 ::     debug=debug)
2010/04/12 04:11:32 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:11:32 ::     self.read(path)
2010/04/12 04:11:32 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:11:32 ::     self._read(fp, filename)
2010/04/12 04:11:32 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:11:32 ::     raise e
2010/04/12 04:11:32 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:11:32 ::     [line 23]: '[]\n'
2010/04/12 04:11:49 :: ---------------------------
2010/04/12 04:11:49 :: wicd initializing...
2010/04/12 04:11:49 :: ---------------------------
2010/04/12 04:11:49 :: wicd is version 1.6.1 426
2010/04/12 04:11:49 :: Traceback (most recent call last):
2010/04/12 04:11:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:11:49 ::     main(sys.argv)
2010/04/12 04:11:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:11:49 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:11:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:11:49 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:11:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:11:49 ::     debug=debug)
2010/04/12 04:11:49 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:11:49 ::     self.read(path)
2010/04/12 04:11:49 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:11:49 ::     self._read(fp, filename)
2010/04/12 04:11:49 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:11:49 ::     raise e
2010/04/12 04:11:49 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:11:49 ::     [line 23]: '[]\n'
2010/04/12 04:12:28 :: ---------------------------
2010/04/12 04:12:28 :: wicd initializing...
2010/04/12 04:12:28 :: ---------------------------
2010/04/12 04:12:28 :: wicd is version 1.6.1 426
2010/04/12 04:12:28 :: Traceback (most recent call last):
2010/04/12 04:12:28 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:12:28 ::     main(sys.argv)
2010/04/12 04:12:28 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:12:28 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:12:28 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:12:28 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:12:28 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:12:28 ::     debug=debug)
2010/04/12 04:12:28 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:12:28 ::     self.read(path)
2010/04/12 04:12:28 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:12:28 ::     self._read(fp, filename)
2010/04/12 04:12:28 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:12:28 ::     raise e
2010/04/12 04:12:28 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:12:28 ::     [line 23]: '[]\n'
2010/04/12 04:12:30 :: ---------------------------
2010/04/12 04:12:30 :: wicd initializing...
2010/04/12 04:12:30 :: ---------------------------
2010/04/12 04:12:30 :: wicd is version 1.6.1 426
2010/04/12 04:12:30 :: Traceback (most recent call last):
2010/04/12 04:12:30 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:12:30 ::     main(sys.argv)
2010/04/12 04:12:30 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:12:30 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:12:30 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:12:30 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:12:30 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:12:30 ::     debug=debug)
2010/04/12 04:12:30 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:12:30 ::     self.read(path)
2010/04/12 04:12:30 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:12:30 ::     self._read(fp, filename)
2010/04/12 04:12:30 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:12:30 ::     raise e
2010/04/12 04:12:30 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:12:30 ::     [line 23]: '[]\n'
2010/04/12 04:13:06 :: ---------------------------
2010/04/12 04:13:06 :: wicd initializing...
2010/04/12 04:13:06 :: ---------------------------
2010/04/12 04:13:06 :: wicd is version 1.6.1 426
2010/04/12 04:13:06 :: Traceback (most recent call last):
2010/04/12 04:13:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:13:06 ::     main(sys.argv)
2010/04/12 04:13:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:13:06 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:13:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:13:06 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:13:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:13:06 ::     debug=debug)
2010/04/12 04:13:06 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:13:06 ::     self.read(path)
2010/04/12 04:13:06 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:13:06 ::     self._read(fp, filename)
2010/04/12 04:13:06 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:13:06 ::     raise e
2010/04/12 04:13:06 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:13:06 ::     [line 23]: '[]\n'
2010/04/12 04:13:45 :: ---------------------------
2010/04/12 04:13:45 :: wicd initializing...
2010/04/12 04:13:45 :: ---------------------------
2010/04/12 04:13:45 :: wicd is version 1.6.1 426
2010/04/12 04:13:46 :: Traceback (most recent call last):
2010/04/12 04:13:46 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:13:46 ::     main(sys.argv)
2010/04/12 04:13:46 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:13:46 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:13:46 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:13:46 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:13:46 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:13:46 ::     debug=debug)
2010/04/12 04:13:46 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:13:46 ::     self.read(path)
2010/04/12 04:13:46 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:13:46 ::     self._read(fp, filename)
2010/04/12 04:13:46 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:13:46 ::     raise e
2010/04/12 04:13:46 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:13:46 ::     [line 23]: '[]\n'
2010/04/12 04:18:05 :: ---------------------------
2010/04/12 04:18:05 :: wicd initializing...
2010/04/12 04:18:05 :: ---------------------------
2010/04/12 04:18:05 :: wicd is version 1.6.1 426
2010/04/12 04:18:05 :: Traceback (most recent call last):
2010/04/12 04:18:05 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 04:18:05 ::     main(sys.argv)
2010/04/12 04:18:05 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 04:18:05 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 04:18:05 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 04:18:05 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 04:18:05 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 04:18:05 ::     debug=debug)
2010/04/12 04:18:05 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 04:18:05 ::     self.read(path)
2010/04/12 04:18:05 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 04:18:05 ::     self._read(fp, filename)
2010/04/12 04:18:05 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 04:18:05 ::     raise e
2010/04/12 04:18:05 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 04:18:05 ::     [line 23]: '[]\n'
2010/04/12 08:59:49 :: ---------------------------
2010/04/12 08:59:49 :: wicd initializing...
2010/04/12 08:59:49 :: ---------------------------
2010/04/12 08:59:49 :: wicd is version 1.6.1 426
2010/04/12 08:59:49 :: Traceback (most recent call last):
2010/04/12 08:59:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 08:59:49 ::     main(sys.argv)
2010/04/12 08:59:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 08:59:49 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 08:59:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 08:59:49 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 08:59:49 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 08:59:49 ::     debug=debug)
2010/04/12 08:59:49 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 08:59:49 ::     self.read(path)
2010/04/12 08:59:49 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 08:59:49 ::     self._read(fp, filename)
2010/04/12 08:59:49 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 08:59:49 ::     raise e
2010/04/12 08:59:49 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 08:59:49 ::     [line 23]: '[]\n'
2010/04/12 09:00:06 :: ---------------------------
2010/04/12 09:00:06 :: wicd initializing...
2010/04/12 09:00:06 :: ---------------------------
2010/04/12 09:00:06 :: wicd is version 1.6.1 426
2010/04/12 09:00:06 :: Traceback (most recent call last):
2010/04/12 09:00:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:00:06 ::     main(sys.argv)
2010/04/12 09:00:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:00:06 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:00:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:00:06 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:00:06 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:00:06 ::     debug=debug)
2010/04/12 09:00:06 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:00:06 ::     self.read(path)
2010/04/12 09:00:06 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:00:06 ::     self._read(fp, filename)
2010/04/12 09:00:06 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:00:06 ::     raise e
2010/04/12 09:00:06 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:00:06 ::     [line 23]: '[]\n'
2010/04/12 09:01:13 :: ---------------------------
2010/04/12 09:01:13 :: wicd initializing...
2010/04/12 09:01:13 :: ---------------------------
2010/04/12 09:01:13 :: wicd is version 1.6.1 426
2010/04/12 09:01:13 :: Traceback (most recent call last):
2010/04/12 09:01:13 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:01:13 ::     main(sys.argv)
2010/04/12 09:01:13 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:01:13 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:01:13 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:01:13 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:01:13 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:01:13 ::     debug=debug)
2010/04/12 09:01:13 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:01:13 ::     self.read(path)
2010/04/12 09:01:13 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:01:13 ::     self._read(fp, filename)
2010/04/12 09:01:13 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:01:13 ::     raise e
2010/04/12 09:01:13 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:01:13 ::     [line 23]: '[]\n'
2010/04/12 09:01:16 :: ---------------------------
2010/04/12 09:01:16 :: wicd initializing...
2010/04/12 09:01:16 :: ---------------------------
2010/04/12 09:01:16 :: wicd is version 1.6.1 426
2010/04/12 09:01:16 :: Traceback (most recent call last):
2010/04/12 09:01:16 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:01:16 ::     main(sys.argv)
2010/04/12 09:01:16 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:01:16 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:01:16 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:01:16 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:01:16 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:01:16 ::     debug=debug)
2010/04/12 09:01:16 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:01:16 ::     self.read(path)
2010/04/12 09:01:16 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:01:16 ::     self._read(fp, filename)
2010/04/12 09:01:16 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:01:16 ::     raise e
2010/04/12 09:01:16 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:01:16 ::     [line 23]: '[]\n'
2010/04/12 09:02:04 :: ---------------------------
2010/04/12 09:02:04 :: wicd initializing...
2010/04/12 09:02:04 :: ---------------------------
2010/04/12 09:02:04 :: wicd is version 1.6.1 426
2010/04/12 09:02:04 :: Traceback (most recent call last):
2010/04/12 09:02:04 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:02:04 ::     main(sys.argv)
2010/04/12 09:02:04 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:02:04 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:02:04 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:02:04 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:02:04 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:02:04 ::     debug=debug)
2010/04/12 09:02:04 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:02:04 ::     self.read(path)
2010/04/12 09:02:04 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:02:04 ::     self._read(fp, filename)
2010/04/12 09:02:04 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:02:04 ::     raise e
2010/04/12 09:02:04 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:02:04 ::     [line 23]: '[]\n'
2010/04/12 09:02:12 :: ---------------------------
2010/04/12 09:02:12 :: wicd initializing...
2010/04/12 09:02:12 :: ---------------------------
2010/04/12 09:02:12 :: wicd is version 1.6.1 426
2010/04/12 09:02:12 :: Traceback (most recent call last):
2010/04/12 09:02:12 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:02:12 ::     main(sys.argv)
2010/04/12 09:02:12 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:02:12 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:02:12 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:02:12 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:02:12 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:02:12 ::     debug=debug)
2010/04/12 09:02:12 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:02:12 ::     self.read(path)
2010/04/12 09:02:12 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:02:12 ::     self._read(fp, filename)
2010/04/12 09:02:12 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:02:12 ::     raise e
2010/04/12 09:02:12 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:02:12 ::     [line 23]: '[]\n'
2010/04/12 09:03:24 :: ---------------------------
2010/04/12 09:03:24 :: wicd initializing...
2010/04/12 09:03:24 :: ---------------------------
2010/04/12 09:03:24 :: wicd is version 1.6.1 426
2010/04/12 09:03:24 :: Traceback (most recent call last):
2010/04/12 09:03:24 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:03:24 ::     main(sys.argv)
2010/04/12 09:03:24 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:03:24 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:03:24 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:03:24 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:03:24 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:03:24 ::     debug=debug)
2010/04/12 09:03:24 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:03:24 ::     self.read(path)
2010/04/12 09:03:24 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:03:24 ::     self._read(fp, filename)
2010/04/12 09:03:24 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:03:24 ::     raise e
2010/04/12 09:03:24 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:03:24 ::     [line 23]: '[]\n'
2010/04/12 09:06:27 :: ---------------------------
2010/04/12 09:06:27 :: wicd initializing...
2010/04/12 09:06:27 :: ---------------------------
2010/04/12 09:06:27 :: wicd is version 1.6.1 426
2010/04/12 09:06:27 :: Traceback (most recent call last):
2010/04/12 09:06:27 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:06:27 ::     main(sys.argv)
2010/04/12 09:06:27 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:06:27 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:06:27 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:06:27 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:06:27 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:06:27 ::     debug=debug)
2010/04/12 09:06:27 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:06:27 ::     self.read(path)
2010/04/12 09:06:27 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:06:27 ::     self._read(fp, filename)
2010/04/12 09:06:27 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:06:27 ::     raise e
2010/04/12 09:06:27 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:06:27 ::     [line 23]: '[]\n'
2010/04/12 09:06:44 :: ---------------------------
2010/04/12 09:06:44 :: wicd initializing...
2010/04/12 09:06:44 :: ---------------------------
2010/04/12 09:06:44 :: wicd is version 1.6.1 426
2010/04/12 09:06:44 :: Traceback (most recent call last):
2010/04/12 09:06:44 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 09:06:44 ::     main(sys.argv)
2010/04/12 09:06:44 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 09:06:44 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 09:06:44 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 09:06:44 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 09:06:44 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 09:06:44 ::     debug=debug)
2010/04/12 09:06:44 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 09:06:44 ::     self.read(path)
2010/04/12 09:06:44 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 09:06:44 ::     self._read(fp, filename)
2010/04/12 09:06:44 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 09:06:44 ::     raise e
2010/04/12 09:06:44 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 09:06:44 ::     [line 23]: '[]\n'
2010/04/12 23:57:51 :: ---------------------------
2010/04/12 23:57:51 :: wicd initializing...
2010/04/12 23:57:51 :: ---------------------------
2010/04/12 23:57:51 :: wicd is version 1.6.1 426
2010/04/12 23:57:51 :: Traceback (most recent call last):
2010/04/12 23:57:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 23:57:51 ::     main(sys.argv)
2010/04/12 23:57:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 23:57:51 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 23:57:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 23:57:51 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 23:57:51 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 23:57:51 ::     debug=debug)
2010/04/12 23:57:51 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 23:57:51 ::     self.read(path)
2010/04/12 23:57:51 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 23:57:51 ::     self._read(fp, filename)
2010/04/12 23:57:51 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 23:57:51 ::     raise e
2010/04/12 23:57:51 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 23:57:51 ::     [line 23]: '[]\n'
2010/04/12 23:58:09 :: ---------------------------
2010/04/12 23:58:09 :: wicd initializing...
2010/04/12 23:58:09 :: ---------------------------
2010/04/12 23:58:09 :: wicd is version 1.6.1 426
2010/04/12 23:58:09 :: Traceback (most recent call last):
2010/04/12 23:58:09 ::   File "/usr/share/wicd/wicd-daemon.py", line 1747, in <module>
2010/04/12 23:58:09 ::     main(sys.argv)
2010/04/12 23:58:09 ::   File "/usr/share/wicd/wicd-daemon.py", line 1711, in main
2010/04/12 23:58:09 ::     daemon = WicdDaemon(wicd_bus, auto_connect=auto_connect)
2010/04/12 23:58:09 ::   File "/usr/share/wicd/wicd-daemon.py", line 87, in __init__
2010/04/12 23:58:09 ::     self.wired_bus= WiredDaemon(bus_name, self, wired=self.wired)
2010/04/12 23:58:09 ::   File "/usr/share/wicd/wicd-daemon.py", line 1327, in __init__
2010/04/12 23:58:09 ::     debug=debug)
2010/04/12 23:58:09 ::   File "/usr/share/wicd/wicd/configmanager.py", line 40, in __init__
2010/04/12 23:58:09 ::     self.read(path)
2010/04/12 23:58:09 ::   File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
2010/04/12 23:58:09 ::     self._read(fp, filename)
2010/04/12 23:58:09 ::   File "/usr/lib/python2.6/ConfigParser.py", line 510, in _read
2010/04/12 23:58:09 ::     raise e
2010/04/12 23:58:09 :: ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.conf
2010/04/12 23:58:09 ::     [line 23]: '[]\n'

---

### Post by chili555 on 2010-04-13
> ConfigParser.ParsingError: File contains parsing errors: /etc/wicd/wired-settings.confLet's see what that file says. It may not have anything to do with our issue, but let's fix it and work out the problems one by one.```
cat /etc/wicd/wired-settings.conf
```It may be more expedient, if you can connect with ethernet, to remove Wicd and reinstall it:```
sudo apt-get remove --purge wicd
sudo apt-get install wicd
```The *--purge* option says, roughly, 'get rid of all my (not working) configuration files, too.'

---

### Post by mlthmp on 2010-04-13
> **chili555 said:**
> ```
sudo apt-get remove --purge wicd
sudo apt-get install wicd
```The *--purge* option says, roughly, 'get rid of all my (not working) configuration files, too.'

That seems to have done it! Thanks! Hopefully this problem won't pop back up again =)

Mike,

---

### Post by chili555 on 2010-04-13
Great! Glad it's working.

---

