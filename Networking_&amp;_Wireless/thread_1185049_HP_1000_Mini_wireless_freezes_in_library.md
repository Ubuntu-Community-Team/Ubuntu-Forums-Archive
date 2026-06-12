---
title: "HP 1000 Mini wireless freezes in library"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by pchachte on 2009-06-11
I'm setting up a HP Mini Mi for my father. Before sending it off, I decided to test the wifi at my local library. (it works perfectly at home).

Every time the computer tries to connect to the wireless system at the library, it freezes completely.

Here is what I believe to be the offending portion of the syslog (sorry if I am including too much):

> Jun 11 15:44:35 paul-umpc NetworkManager: <info>  starting... 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/net_00_24_2c_81_13_e2 
Jun 11 15:44:35 paul-umpc kernel: [   52.896090] sky2 eth0: enabling interface
Jun 11 15:44:35 paul-umpc kernel: [   52.902208] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Deactivating device eth0. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  wlan0: Device is fully-supported using driver 'wl'. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Deactivating device wlan0. 
Jun 11 15:44:35 paul-umpc NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device wlan0: Invalid argument 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 11 15:44:35 paul-umpc NetworkManager: <info>  Wireless now enabled by radio killswitch 
Jun 11 15:44:36 paul-umpc kernel: [   53.616679] ppdev: user-space parallel port driver
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Jun 11 15:44:46 paul-umpc dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Will activate connection 'wlan0/EPL - terms at: wireless.epl.org'. 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Device wlan0 activation scheduled... 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0) started... 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jun 11 15:44:46 paul-umpc NetworkManager: <info>  Activation (wlan0/wireless): access point 'EPL - terms at: wireless.epl.org' is unencrypted, no key needed. 
Jun 11 15:44:47 paul-umpc NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Jun 11 15:44:47 paul-umpc NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 11 15:44:47 paul-umpc kernel: [   65.544306] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 11 15:44:47 paul-umpc NetworkManager: <info>  SUP: response was 'OK' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: response was 'OK' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: response was '0' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 45504c202d207465726d732061743a20776972656c6573732e65706c2e6f7267' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: response was 'OK' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: response was 'OK' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  SUP: response was 'OK' 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jun 11 15:44:48 paul-umpc kernel: [   65.826261] wlan0 (WE) : Wireless Event too big (33)
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  Supplicant state changed: 1 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'EPL - terms at: wireless.epl.org'. 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 11 15:44:48 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Jun 11 15:44:49 paul-umpc NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Jun 11 15:44:49 paul-umpc NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Jun 11 15:44:49 paul-umpc NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Jun 11 15:44:49 paul-umpc avahi-daemon[4283]: Registering new address record for fe80::224:2cff:fe81:13e2 on wlan0.*.
Jun 11 15:44:50 paul-umpc NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Jun 11 15:44:54 paul-umpc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun 11 15:44:54 paul-umpc dhclient: DHCPOFFER of 192.168.1.39 from 192.168.1.254
Jun 11 15:44:54 paul-umpc dhclient: DHCPREQUEST of 192.168.1.39 on wlan0 to 255.255.255.255 port 67
Jun 11 15:44:54 paul-umpc dhclient: DHCPACK of 192.168.1.39 from 192.168.1.254
Jun 11 15:44:54 paul-umpc dhclient: bound to 192.168.1.39 -- renewal in 6985 seconds.
Jun 11 15:44:55 paul-umpc NetworkManager: <info>  Supplicant state changed: 1 
Jun 11 15:45:54 paul-umpc esd: biquad loaded...
Jun 11 15:45:54 paul-umpc avahi-daemon[4283]: Disconnected from D-Bus, exiting.
Jun 11 15:45:54 paul-umpc avahi-daemon[4283]: Got SIGQUIT, quitting.
Jun 11 15:45:54 paul-umpc dhcdbd: Shut down.
Jun 11 15:45:54 paul-umpc hcid[4492]: Got disconnected from the system message bus
Jun 11 15:45:54 paul-umpc audio[4499]: Removing service record 0x10000 failed: Connection is closed
Jun 11 15:45:54 paul-umpc audio[4499]: Unregistered manager path
Jun 11 15:45:54 paul-umpc audio[4499]: Exit
Jun 11 15:45:54 paul-umpc input[4500]: Unregistered manager path
Jun 11 15:45:54 paul-umpc input[4500]: Exit
Jun 11 15:45:54 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:45:57 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:45:57 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:45:59 paul-umpc hcid[4492]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Jun 11 15:46:00 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:00 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:03 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:03 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:04 paul-umpc hcid[4492]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Jun 11 15:46:06 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:06 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:09 paul-umpc hcid[4492]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Jun 11 15:46:09 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:09 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:12 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:12 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:14 paul-umpc hcid[4492]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Jun 11 15:46:15 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:15 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:18 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:18 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:19 paul-umpc hcid[4492]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Jun 11 15:46:21 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:21 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:22 paul-umpc NetworkManager: nm_dbus_signal_device_strength_change: assertion `connection != NULL' failed
Jun 11 15:46:24 paul-umpc hcid[4492]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
Jun 11 15:46:24 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:24 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 
Jun 11 15:46:27 paul-umpc console-kit-daemon[4336]: WARNING: Couldn't connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
Jun 11 15:46:27 paul-umpc NetworkManager: <WARN>  nm_dbus_init(): nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running! 

Thanks for your help.

---

