---
title: "wminput blocks wifi connection"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by cspollard on 2009-07-09
Hello,

I'm having a strange problem with the wiimote input program wminput.  I have a Dell Vostro 1400 with built-in wifi and bluetooth, and I've never had this problem before.  But a few days ago I found that whenever my wiimote was connected (usually I use it for Boxee), I couldn't connect to any wireless networks.  This is very strange considering the only direct connection I can think of between bluetooth and wifi on my laptop is the hardware switch that controls both of them (one has to turn them off individually in software, otherwise they are linked).

Either way, when I kill wminput, sure enough I am able to connect to wireless networks again.  When I'm already connected to a network and then start wminput, often page loads time out, but I'm not sure if there is a 100% correlation there.

Edit: In fact, I can't load any websites while wminput is running in daemon mode--all network traffic seems to be blocked while wminput is waiting for the wiimote to connect.  Once the wiimote is connected, everything is fine again, and once it is disconnected, all websites are blocked again.  Strange, no?

Thanks for any help you can give!

Here is the output from /var/log/daemon.log (just so you know, there is a link to a launchpad bug in the output, but I've followed it and it seems unrelated):

> Jul  9 16:54:06 xxxxxxxx acpid: client connected from 2791[111:120] 
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Bluetooth daemon
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Starting SDP server
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: bridge pan0 created
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Registered interface org.bluez.Service on path /org/bluez/2817/any
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Starting experimental netlink support
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Failed to find Bluetooth netlink family
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: HCI dev 0 registered
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: HCI dev 0 up
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Starting security manager 0
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/2817/hci0
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Registered interface org.bluez.NetworkPeer on path /org/bluez/2817/hci0
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Registered interface org.bluez.NetworkHub on path /org/bluez/2817/hci0
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Registered interface org.bluez.NetworkRouter on path /org/bluez/2817/hci0
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Registered interface org.bluez.Service on path /org/bluez/2817/hci0
Jul  9 16:54:06 xxxxxxxx bluetoothd[2817]: Adapter /org/bluez/2817/hci0 has been enabled
Jul  9 16:54:07 xxxxxxxx acpid: client connected from 2861[0:0] 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  starting... 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4222_rfkill_3945ABG_wlan 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  (eth0): new Ethernet device (driver: 'tg3') 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1e_c9_02_45_88 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1c_bf_99_78_03 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  Trying to start the supplicant... 
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  Trying to start the system settings daemon... 
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: init!
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1e_c9_02_45_88, iface: eth0): not well known
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_1c_bf_99_78_03, iface: wlan0): not well known
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jul  9 16:54:07 xxxxxxxx nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul  9 16:54:07 xxxxxxxx nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: (139486520) ... get_connections.
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    SCPlugin-Ifupdown: (139486520) ... get_connections (managed=false): return empty list.
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Found user 'avahi' (UID 110) and group 'avahi' (GID 119).
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Successfully dropped root privileges.
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: avahi-daemon 0.6.23 starting up.
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Successfully called chroot().
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Successfully dropped remaining capabilities.
Jul  9 16:54:07 xxxxxxxx nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: No service file found in /etc/avahi/services.
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Network interface enumeration completed.
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Registering HINFO record with values 'I686'/'LINUX'.
Jul  9 16:54:07 xxxxxxxx avahi-daemon[2909]: Server startup complete. Host name is xxxxxxxx.local. Local service cookie is 2578896059.
Jul  9 16:54:07 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (eth0): bringing up device. 
Jul  9 16:54:12 xxxxxxxx nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1e_c9_02_45_88
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (eth0): preparing device. 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (wlan0): bringing up device. 
Jul  9 16:54:12 xxxxxxxx acpid: client connected from 2861[0:0] 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (wlan0): preparing device. 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Jul  9 16:54:12 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready 
Jul  9 16:54:25 xxxxxxxx console-kit-daemon[2649]: WARNING: Couldn't read /proc/2648/environ: Failed to open file '/proc/2648/environ': No such file or directory 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) starting connection 'Auto xxx' 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto xxx' requires no security.  No secrets needed. 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Config: added 'ssid' value 'xxx' 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  Config: set interface ap_scan to 1 
Jul  9 16:54:39 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected 
Jul  9 16:54:40 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jul  9 16:54:43 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jul  9 16:54:53 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jul  9 16:54:53 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jul  9 16:54:54 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jul  9 16:54:54 xxxxxxxx NetworkManager: <info>  wlan0: link timed out. 
Jul  9 16:55:04 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected 
Jul  9 16:55:04 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Jul  9 16:55:20 xxxxxxxx NetworkManager: <info>  wlan0: link timed out. 
Jul  9 16:55:34 xxxxxxxx NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  Activation (wlan0) failed for access point (xxx) 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  Marking connection 'Auto xxx' invalid. 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  Activation (wlan0) failed. 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jul  9 16:55:40 xxxxxxxx NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 


---

### Post by cspollard on 2009-07-10
Bump?  I've tried a few things, but nothing fixes the problems.  Does anyone even have an idea of where to look for another logfile that might show me what the problem is?

---

### Post by cspollard on 2009-07-18
mmmmmm...searched google for a while and still nothing.  Has anyone even heard of this issue?

---

### Post by Mechaphoenix25 on 2010-09-16
I have this exact same problem, with both of my Dell laptops - an old Inspiron 1501 now in service as an HTPC, as well as a new Studio 1558.  Not only does the wminput block wifi for the computer it's connected to, any computer within about a 15 foot radius is affected.  Where would a good place to file a bug report be?

---

### Post by cspollard on 2010-09-16
Hey,

It's been a long time, and I don't currently have access to this system.  Sorry!  I didn't know where to file a bug, and I didn't get any help, so I just left the problem  :D

I would say make a launchpad bug.  I never found one related to this, and I doubt a new one's been made.  I would do it myself, but I really need access to the computer to be of any use :)

Cheers.

---

### Post by jacksenechal on 2011-06-01
Launchpad bug submitted: [https://bugs.launchpad.net/ubuntu/+source/cwiid/+bug/791661](https://bugs.launchpad.net/ubuntu/+source/cwiid/+bug/791661)

---

### Post by Rebelli0us on 2011-09-08
wminput with daemon option crashes my system, but works fine without the -d in command line. I've posted details here:

[http://ubuntuforums.org/showthread.php?t=1708155]("http://ubuntuforums.org/showthread.php?t=1708155")


//

---

