---
title: "Cannot get DHCP working on wireless connection"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by chiefmac70 on 2010-08-31
I've been battling for some days now with trying to get a Dynamode Wireless USB adaptor working (it uses the Ralink RT3070 chipset). The machine is a fresh install of Ubuntu 10.04, network manager reports that a connection to Steve_Mac_D_Link_Router has been established and is active, but I cannot connect to the internet or ping even my router. I know the router is fine as I'm sitting here with my laptop happily connected by its wireless connection. I've put below all the info that seems relevant after my forum searches.

I can see the problem is DHCP related as there is no gateway set-up (router is 192.168.0.1). If I run

```
sudo dhclient wlan1
```it does 6 DHCPDISCOVER and then goes to sleep as it gets no answer.

I tried 

```
sudo route add default gw 192.168.0.1 wlan1
```but get SIOCADDRT: No such process.

Any help much appreciated! I'm at the end of what I can do and I've tried so many things. I have deliberately not tried wicd instead of network manager yet as the problem looks more fundamental than that, but please feel free to correct me as I'm no expert!

iwconfig:

```
wlan1     IEEE 802.11bgn  ESSID:"Steve_Mac_D_Link_Router"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 86:F8:11:28:54:23   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```ifconfig -a:

```

eth0      Link encap:Ethernet  HWaddr 00:19:66:60:b2:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57952 (57.9 KB)  TX bytes:57952 (57.9 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0c:43:30:89:a5  
          inet6 addr: fe80::20c:43ff:fe30:89a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:25770 (25.7 KB)

wlan1:avahi Link encap:Ethernet  HWaddr 00:0c:43:30:89:a5  
          inet addr:169.254.7.128  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```/etc/network

What is the wlan1:avahi item above? Is it a problem?

/interfaces:

```

auto lo
iface lo inet loopback
# address 127.0.0.1
# netmask 255.0.0.0
# network 192.168.0.0
# broadcast 192.168.0.255
# gateway 192.168.0.1
# auto wlan1
# iface wlan1 inet dhcp
```route -n:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan1
```sudo dhclient wlan1:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan1/00:0c:43:30:89:a5
Sending on   LPF/wlan1/00:0c:43:30:89:a5
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by MaindotC on 2010-08-31
The outpu from iwconfig indicates that your wireless adapter is working from an electrical standpoint and can detect wireless networks, and in fact it is associated with the wireless access point on which I'm assuming your laptop is connected.

The only entry with which you should be concerned in ifconfig is wlan1 and as you correctly pointed out it has not received an ip address (via dhcp) from your access point.  Just fyi, any network device that tries and does not receive dhcp information will assign itself a 169 address (which is defined in open standards such as IEEE docs) so you'll see that address for devices that can't pull dhcp.  Same thing with the routing table - that's just filler.

I believe your /etc/network/interfaces file is correct because it's the same one I have for my laptop.  The output from dhclient is typical for being unable to pull dhcp.  It sends out a request and if it doesn't receive a reply from the access point then it stops trying.

Can you open your syslog and view the entries?  You should see timestamps with those entries.  Try using the [Network manager applet](http://projects.gnome.org/NetworkManager/) to select your wireless network then monitor the syslog and see if there are any error messages that indicate a problem receiving the dhcp, or a rejection or anything that would indicate the problem.

It is strange because your wireless card is associated with the access point - meaning it knows it's there and it's communicating at least up to layer 2 - but that network information (DHCP) isn't coming across.  Is there any chance you may have MAC filtering set on the access point - only allowing certain devices to connect?

---

### Post by chiefmac70 on 2010-08-31
Thanks for the reply. MAC filtering was a good idea, but I'm afraid that's not the issue - I've checked to be sure. As for syslog, I've had a look through and spot two things that leave me wondering:

```
wpa_supplicant[889]: Failed to initiate AP scan.

```This was part of the initial start-up. Why should it fail?

A little bit later, there's this:

```
NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed

```I have no idea what this means, but it occurs twice during start-up! Later, after I changed some settings, it occurred again. Any ideas? The full log follows:

```
Aug 31 20:39:07 bethmac-desktop kernel: [    9.578419] Registered led device: rt2800usb-phy0::radio
Aug 31 20:39:07 bethmac-desktop kernel: [    9.578435] Registered led device: rt2800usb-phy0::assoc
Aug 31 20:39:07 bethmac-desktop kernel: [    9.578450] Registered led device: rt2800usb-phy0::quality
Aug 31 20:39:07 bethmac-desktop kernel: [    9.578802] usbcore: registered new interface driver rt2800usb
Aug 31 20:39:07 bethmac-desktop kernel: [    9.616880] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Aug 31 20:39:07 bethmac-desktop kernel: [    9.624490] rtusb init --->
Aug 31 20:39:07 bethmac-desktop kernel: [    9.624613] usbcore: registered new interface driver rt2870
Aug 31 20:39:07 bethmac-desktop cron[955]: (CRON) INFO (pidfile fd = 3)
Aug 31 20:39:07 bethmac-desktop init: apport pre-start process (949) terminated with status 1
Aug 31 20:39:07 bethmac-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/net/wlan1, iface: wlan1)
Aug 31 20:39:07 bethmac-desktop kernel: [    9.767103] udev: renamed network interface wlan0 to wlan1
Aug 31 20:39:07 bethmac-desktop kernel: [    9.768390] rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
Aug 31 20:39:07 bethmac-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:02.1/usb1/1-7/1-7:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Aug 31 20:39:07 bethmac-desktop NetworkManager: <info>  (wlan1): driver supports SSID scans (scan_capa 0x01).
Aug 31 20:39:07 bethmac-desktop NetworkManager: <info>  (wlan1): new 802.11 WiFi device (driver: 'rt2800usb')
Aug 31 20:39:07 bethmac-desktop NetworkManager: <info>  (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 31 20:39:07 bethmac-desktop NetworkManager: <info>  (wlan1): now managed
Aug 31 20:39:07 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 1 -> 2 (reason 2)
Aug 31 20:39:07 bethmac-desktop NetworkManager: <info>  (wlan1): bringing up device.
Aug 31 20:39:07 bethmac-desktop acpid: starting up with proc fs
Aug 31 20:39:07 bethmac-desktop cron[968]: (CRON) STARTUP (fork ok)
Aug 31 20:39:07 bethmac-desktop anacron[966]: Anacron 2.3 started on 2010-08-31
Aug 31 20:39:07 bethmac-desktop acpid: 36 rules loaded
Aug 31 20:39:07 bethmac-desktop acpid: waiting for events: event logging is off
Aug 31 20:39:07 bethmac-desktop cron[968]: (CRON) INFO (Running @reboot jobs)
Aug 31 20:39:07 bethmac-desktop init: apport post-stop process (981) terminated with status 1
Aug 31 20:39:07 bethmac-desktop kernel: [    9.890562] [drm] nouveau 0000:00:0d.0: Allocating FIFO number 1
Aug 31 20:39:07 bethmac-desktop kernel: [    9.890807] [drm] nouveau 0000:00:0d.0: nouveau_channel_alloc: initialised FIFO 1
Aug 31 20:39:08 bethmac-desktop anacron[966]: Normal exit (0 jobs run)
Aug 31 20:39:08 bethmac-desktop kernel: [   10.131967] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Aug 31 20:39:08 bethmac-desktop NetworkManager: <info>  (wlan1): preparing device.
Aug 31 20:39:08 bethmac-desktop NetworkManager: <info>  (wlan1): deactivating device (reason: 2).
Aug 31 20:39:08 bethmac-desktop anacron[1123]: Anacron 2.3 started on 2010-08-31
Aug 31 20:39:08 bethmac-desktop anacron[1123]: Normal exit (0 jobs run)
Aug 31 20:39:08 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant interface state:  starting -> ready
Aug 31 20:39:08 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 2 -> 3 (reason 42)
Aug 31 20:39:08 bethmac-desktop wpa_supplicant[889]: Failed to initiate AP scan.
Aug 31 20:39:08 bethmac-desktop init: plymouth-stop pre-start process (1152) terminated with status 1
Aug 31 20:39:09 bethmac-desktop gdm-session-worker[1160]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Sucessfully called chroot.
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Sucessfully dropped privileges.
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Sucessfully limited resources.
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Running.
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Canary thread running.
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Watchdog thread running.
Aug 31 20:39:09 bethmac-desktop polkitd[1172]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1166 of process 1166 (n/a) owned by '114' high priority at nice level -11.
Aug 31 20:39:09 bethmac-desktop rtkit-daemon[1168]: Supervising 1 threads of 1 processes of 1 users.
Aug 31 20:39:10 bethmac-desktop kernel: [   12.399012] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
Aug 31 20:39:10 bethmac-desktop kernel: [   12.403592] generic-usb 0003:046D:C214.0001: timeout initializing reports
Aug 31 20:39:10 bethmac-desktop kernel: [   12.403682] input: Logitech Logitech Attack 3 as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input6
Aug 31 20:39:10 bethmac-desktop kernel: [   12.403768] generic-usb 0003:046D:C214.0001: input,hidraw0: USB HID v1.10 Joystick [Logitech Logitech Attack 3] on usb-0000:00:02.0-2/input0
Aug 31 20:39:10 bethmac-desktop kernel: [   12.403799] usbcore: registered new interface driver usbhid
Aug 31 20:39:10 bethmac-desktop kernel: [   12.403802] usbhid: v2.6:USB HID core driver
Aug 31 20:39:10 bethmac-desktop anacron[1212]: Anacron 2.3 started on 2010-08-31
Aug 31 20:39:10 bethmac-desktop anacron[1212]: Normal exit (0 jobs run)
Aug 31 20:39:10 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1239 of process 1166 (n/a) owned by '114' RT at priority 5.
Aug 31 20:39:10 bethmac-desktop rtkit-daemon[1168]: Supervising 2 threads of 1 processes of 1 users.
Aug 31 20:39:10 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1240 of process 1166 (n/a) owned by '114' RT at priority 5.
Aug 31 20:39:10 bethmac-desktop rtkit-daemon[1168]: Supervising 3 threads of 1 processes of 1 users.
Aug 31 20:39:10 bethmac-desktop gdm-simple-greeter[1158]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Aug 31 20:39:11 bethmac-desktop acpid: client connected from 1265[108:114]
Aug 31 20:39:11 bethmac-desktop acpid: 1 client rule loaded
Aug 31 20:39:13 bethmac-desktop gdm-session-worker[1160]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1353 of process 1353 (n/a) owned by '1000' high priority at nice level -11.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Supervising 4 threads of 2 processes of 2 users.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1370 of process 1353 (n/a) owned by '1000' RT at priority 5.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Supervising 5 threads of 2 processes of 2 users.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1377 of process 1353 (n/a) owned by '1000' RT at priority 5.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Supervising 6 threads of 2 processes of 2 users.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Sucessfully made thread 1381 of process 1381 (n/a) owned by '1000' high priority at nice level -11.
Aug 31 20:39:26 bethmac-desktop rtkit-daemon[1168]: Supervising 7 threads of 3 processes of 2 users.
Aug 31 20:39:26 bethmac-desktop pulseaudio[1381]: pid.c: Daemon already running.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) starting connection 'Steve_Mac_D_Link_Router'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 3 -> 4 (reason 0)
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): access point 'Steve_Mac_D_Link_Router' has security, but secrets are required.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 6 -> 4 (reason 0)
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): connection 'Steve_Mac_D_Link_Router' has security, and secrets exist.  No new secrets needed.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'ssid' value 'Steve_Mac_D_Link_Router'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'mode' value '1'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'frequency' value '2412'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-NONE'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'proto' value 'WPA'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'pairwise' value 'NONE'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: added 'group' value 'TKIP'
Aug 31 20:39:26 bethmac-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 31 20:39:26 bethmac-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  Config: set interface ap_scan to 2
Aug 31 20:39:26 bethmac-desktop wpa_supplicant[889]: Trying to associate with SSID 'Steve_Mac_D_Link_Router'
Aug 31 20:39:26 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  inactive -> scanning
Aug 31 20:39:27 bethmac-desktop wpa_supplicant[889]: Association request to the driver failed
Aug 31 20:39:27 bethmac-desktop wpa_supplicant[889]: CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (auth) [id=-1 id_str=]
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associating
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> completed
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Steve_Mac_D_Link_Router'.
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 5 -> 7 (reason 0)
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) started...
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) started...
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 31 20:39:27 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Joining mDNS multicast group on interface wlan1.IPv4 with address 10.42.43.1.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: New relevant interface wlan1.IPv4 for mDNS.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Registering new address record for 10.42.43.1 on wlan1.IPv4.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Interface wlan1.IPv4 no longer relevant for mDNS.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 10.42.43.1.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Withdrawing address record for 10.42.43.1 on wlan1.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Joining mDNS multicast group on interface wlan1.IPv4 with address 10.42.43.1.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: New relevant interface wlan1.IPv4 for mDNS.
Aug 31 20:39:27 bethmac-desktop avahi-daemon[758]: Registering new address record for 10.42.43.1 on wlan1.IPv4.
Aug 31 20:39:28 bethmac-desktop kernel: [   30.069601] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 31 20:39:28 bethmac-desktop kernel: [   30.088854] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Aug 31 20:39:28 bethmac-desktop kernel: [   30.089746] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Aug 31 20:39:28 bethmac-desktop kernel: [   30.089750] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Aug 31 20:39:28 bethmac-desktop kernel: [   30.089752] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan1 --protocol tcp --destination-port 53 --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan1 --protocol udp --destination-port 53 --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan1 --protocol tcp --destination-port 67 --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan1 --protocol udp --destination-port 67 --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan1 --jump REJECT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --out-interface wlan1 --jump REJECT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan1 --out-interface wlan1 --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan1 --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan1 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Starting dnsmasq...
Aug 31 20:39:28 bethmac-desktop NetworkManager: <debug> [1283283568.385885] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-wlan1.pid
Aug 31 20:39:28 bethmac-desktop NetworkManager: <debug> [1283283568.396478] nm_dnsmasq_manager_start(): dnsmasq started with pid 1437
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 7 -> 8 (reason 0)
Aug 31 20:39:28 bethmac-desktop NetworkManager: <debug> [1283283568.396906] periodic_update(): Roamed from BSSID 00:00:00:00:00:00 (Steve_Mac_D_Link_Router) to (none) ((none))
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Activation (wlan1) successful, device activated.
Aug 31 20:39:28 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Aug 31 20:39:28 bethmac-desktop dnsmasq[1437]: started, version 2.52 cachesize 150
Aug 31 20:39:28 bethmac-desktop dnsmasq[1437]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Aug 31 20:39:28 bethmac-desktop dnsmasq-dhcp[1437]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Aug 31 20:39:28 bethmac-desktop dnsmasq[1437]: no servers found in /etc/resolv.conf, will retry
Aug 31 20:39:28 bethmac-desktop dnsmasq[1437]: cleared cache
Aug 31 20:39:28 bethmac-desktop avahi-daemon[758]: Registering new address record for fe80::20c:43ff:fe30:89a5 on wlan1.*.
Aug 31 20:39:29 bethmac-desktop ntpdate[1467]: can't find host ntp.ubuntu.com
Aug 31 20:39:29 bethmac-desktop ntpdate[1467]: no servers can be used, exiting
Aug 31 20:39:34 bethmac-desktop kernel: [   36.816038] wlan1: Creating new IBSS network, BSSID 8e:c8:fe:d5:2f:d4
Aug 31 20:39:34 bethmac-desktop wpa_supplicant[889]: Associated with 8e:c8:fe:d5:2f:d4
Aug 31 20:39:34 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  completed -> associated
Aug 31 20:39:34 bethmac-desktop wpa_supplicant[889]: CTRL-EVENT-CONNECTED - Connection to 8e:c8:fe:d5:2f:d4 completed (reauth) [id=0 id_str=]
Aug 31 20:39:34 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> completed
Aug 31 20:39:37 bethmac-desktop kernel: [   39.720017] wlan1: no IPv6 routers present
Aug 31 20:39:38 bethmac-desktop kernel: [   40.856556] end_request: I/O error, dev fd0, sector 0
Aug 31 20:39:51 bethmac-desktop kernel: [   53.032414] end_request: I/O error, dev fd0, sector 0
Aug 31 20:40:09 bethmac-desktop kernel: [   71.160035] Clocksource tsc unstable (delta = -291494624 ns)
Aug 31 20:40:28 bethmac-desktop AptDaemon: INFO: Initializing daemon
Aug 31 20:44:35 bethmac-desktop kernel: [  337.000166] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:45:29 bethmac-desktop AptDaemon: INFO: Quiting due to inactivity
Aug 31 20:45:29 bethmac-desktop AptDaemon: INFO: Shutdown was requested
Aug 31 20:45:35 bethmac-desktop kernel: [  397.000182] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:46:35 bethmac-desktop kernel: [  456.988219] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:47:35 bethmac-desktop kernel: [  517.000226] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:48:35 bethmac-desktop kernel: [  577.000137] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:49:35 bethmac-desktop kernel: [  637.000054] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:50:35 bethmac-desktop kernel: [  697.000182] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Aug 31 20:51:35 bethmac-desktop kernel: [  757.000049] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)


Below is result of editing the connection in Network Mgr and changing Mode from Ad Hoc to Infrastructure:
=========================================================================================================

Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 8 -> 3 (reason 38)
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): deactivating device (reason: 38).
Aug 31 20:56:40 bethmac-desktop avahi-daemon[758]: Withdrawing address record for 10.42.43.1 on wlan1.
Aug 31 20:56:40 bethmac-desktop avahi-daemon[758]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 10.42.43.1.
Aug 31 20:56:40 bethmac-desktop dnsmasq[1755]: exiting on receipt of SIGTERM
Aug 31 20:56:40 bethmac-desktop avahi-daemon[758]: Interface wlan1.IPv4 no longer relevant for mDNS.
Aug 31 20:56:40 bethmac-desktop kernel: [ 1062.509584] wlan1: Trigger new scan to find an IBSS to join
Aug 31 20:56:40 bethmac-desktop NetworkManager: <WARN>  nm_device_wifi_set_mode(): error setting card wlan1 to mode 2: Device or resource busy
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan1 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan1 --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface wlan1 --out-interface wlan1 --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --out-interface wlan1 --jump REJECT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete FORWARD --in-interface wlan1 --jump REJECT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan1 --protocol udp --destination-port 67 --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan1 --protocol tcp --destination-port 67 --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan1 --protocol udp --destination-port 53 --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan1 --protocol tcp --destination-port 53 --jump ACCEPT
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) starting connection 'Steve_Mac_D_Link_Router'
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 3 -> 4 (reason 0)
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): access point 'Steve_Mac_D_Link_Router' has security, but secrets are required.
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 6 -> 4 (reason 0)
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): connection 'Steve_Mac_D_Link_Router' has security, and secrets exist.  No new secrets needed.
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Config: added 'ssid' value 'Steve_Mac_D_Link_Router'
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 31 20:56:40 bethmac-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 31 20:56:40 bethmac-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 31 20:56:40 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Aug 31 20:56:43 bethmac-desktop NetworkManager: <debug> [1283284603.000619] ensure_killed(): waiting for dnsmasq pid 1755 to exit
Aug 31 20:56:43 bethmac-desktop NetworkManager: <debug> [1283284603.000806] ensure_killed(): dnsmasq pid 1755 cleaned up
Aug 31 20:57:41 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): association took too long.
Aug 31 20:57:41 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Aug 31 20:57:41 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): asking for new secrets
Aug 31 20:57:41 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 6 -> 4 (reason 0)
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  (wlan1): device state change: 4 -> 5 (reason 0)
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1/wireless): connection 'Steve_Mac_D_Link_Router' has security, and secrets exist.  No new secrets needed.
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Config: added 'ssid' value 'Steve_Mac_D_Link_Router'
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug 31 20:57:45 bethmac-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 31 20:57:45 bethmac-desktop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  Config: set interface ap_scan to 1
Aug 31 20:57:45 bethmac-desktop NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning

```

---

### Post by MaindotC on 2010-08-31
I googled "NM_IS_SETTING_802_1X" and the best I can find now are two suggestions that I think have nothing to do with your issue:

Try to increase the transmission power on your AP (and I know you said one of your laptops was working just fine so I apologize for this suggestion).

Disable uPnP in the AP.

Also please post the output of:
```

lshw -C network

```

I'll be #ubuntu-us-ny for a few hours if you want to chat live.

---

### Post by chiefmac70 on 2010-09-01
Sorry strAlan, but still no better :( The power on the AP was already at 100% (and my laptop reports about 95% signal strength when next to the troublesome PC). I've also turned off universal PnP and that makes no difference. Here's the result of sudo lshw -C network:

```

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0c:43:30:89:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bgn
```

Thanks for the offer of live chat, but it's not going to happen often as I'm in the UK so asleep for half of your waking day (assuming you're US)! Thanks anyway. I can't see anything informative above. Any more ideas...?

---

### Post by 4ebees on 2010-09-01
> **chiefmac70 said:**
> Sorry strAlan, but still no better :( The power on the AP was already at 100% (and my laptop reports about 95% signal strength when next to the troublesome PC). I've also turned off universal PnP and that makes no difference. Here's the result of sudo lshw -C network:

```

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0c:43:30:89:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bgn
```

Thanks for the offer of live chat, but it's not going to happen often as I'm in the UK so asleep for half of your waking day (assuming you're US)! Thanks anyway. I can't see anything informative above. Any more ideas...?

One quick question - was the router being used previously by some other device or is this a fresh set-up?

I'm asking purely because my wireless router requires me to switch off DHCP and allow my modem (to which the router is connected) to give out addresses.

My set up goes:

Telephone line :))
Modem
LAN to router
Signal to laptop

I've come across this issue a couple of times in the past and so thought I'd share :))

---

### Post by MaindotC on 2010-09-01
> **chiefmac70 said:**
> ```

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0c:43:30:89:a5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bgn
```

Bah, that was supposed to list your wireless card driver like this:```


*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:4a:1c:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **[SIZE="4"]driver=iwl3945[/SIZE]** ip=149.119.200.114 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
```

Is your network card pci or usb?

---

### Post by bkratz on 2010-09-01
Sorry to interrupt, but is this really the problem?

wlan1     IEEE 802.11bgn  ESSID:"Steve_Mac_D_Link_Router"  
         [COLOR="Red"] Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: 86:F8:11:28:54:23   
          Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


Ad-hoc is used between computers. If you agree @StrAlan you could have him/she try

sudo iwconfig wlan1 mode Managed

Sorry if I have interrupted unnecessarily.

---

### Post by MaindotC on 2010-09-01
Whoa, good eye there kratz.  Yes it definitely should be in "managed" mode, not ad-hoc.  If your machine is going into ad-hoc on boot then you'll need to find the configuration that is setting that and change it to managed.  That definitely would explain the issue.

---

### Post by chiefmac70 on 2010-09-02
Thanks to all for new pointers:

4ebees, no the DHCP server is always run on my router. I know this because I have two laptops in the house, 1 only 6 months old, and they each pick up addresses from it regularly. I also know because, to add salt to the wound, I had forgotten that the PC I'm working on has Windows 7 (yuck) on it and the wireless card I'm using works just fine under Windows, picking up the DHCP server and hence an address immediately with no intervention. Hey, I'm no Windoze fan, but I can't ignore the fact that this thing just WORKS under bad old MS...

strAlan, my network card is USB, yes.

bkratz, very helpful point here. I noticed after easily getting the wireless working under (cough) Windows, that it set itself up as Infrastructure and so I tried switching to this under Ubuntu. Sadly, it doesn't work. I did sudo iwconfig wlan1 mode Managed and changed the mode under Network Manager to Managed (why don't the two settings seem to affect each other at all?). Now, I can see no connection under Network Manager at all. I also tried iwlist wlan1 scanning but it gives me "wlan1  No scan results"

So, now I've got the correct mode set up and I can see nothing!! :icon_frown: I used iwconfig to set the SSID to Steve_Mac_D_Link_Router but that doesn't help either.

So what on earth do I do next? Should I try wicd? Should I look to building device drivers from the ralink website (how do I check which driver is being used now?)? Suggestions pls?

Thanks guys for all your support. Still no progress yet though...

---

### Post by CharlesA on 2010-09-02
Not that it'll help, but whenever I boot into ubuntu, I can connect fine from network manager, as long as I can see the network, I can connect. I get prompted for the passphrase.

That's using both onboard and usb wireless cards.

---

### Post by MaindotC on 2010-09-02
> **chiefmac70 said:**
> strAlan, my network card is USB, yes.


Let's take a look at your card specs.  It will help determine the driver.  Post:

lsusb

---

### Post by chiefmac70 on 2010-09-03
Ok, here's the output of lsusb plus the section of lsusb -v for the Ralink USB network card in question (the device IDs are only different because I plugged in a USB memory stick to copy the results across to a machine with internet access ;-) ):

```
Bus 002 Device 002: ID 046d:c214 Logitech, Inc. ATK3 (Attack III Joystick)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x3070 
  bcdDevice            1.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

---

### Post by MaindotC on 2010-09-04
Ok, you should have a driver called rt2870 or something close to that.  Post the output of ```
lsmod
``` or if you see something in that list that begins with rt just paste it here.

---

### Post by chiefmac70 on 2010-09-07
Sorry for the delay in responding. Here's the output of 'lsmod | grep rt'

```
rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
parport_pc             25962  1 
crc_ccitt               1339  1 rt2800usb
agpgart                31724  2 ttm,drm
parport                32635  3 ppdev,parport_pc,lp
```

Is it significant that rt2870sta has a use count of zero? This is the driver that Windows installed for my USB card. What increments this use count?

---

### Post by MaindotC on 2010-09-07
According to [this document which I found by googling](http://ldn.linuxfoundation.org/node/12626) use count indicates how many other modules are using that particular module.  It doesn't seem to increment each time it is used, if that's what you were wondering.

I'm getting out of the refined troubleshooting mode and more into the throwing-darts (suggesting random troubleshooting tips) mode.  Some of these are dumb questions but here goes:  Do you have a killswitch on the device (i'm assuming this is another laptop)?  Have you tried plugging it into a different usb port (should make absolutely no difference but what the hell why not)?  Is your AP set to issue dhcp?  Can you run Wireshark (let me know if you're not familiar with this) and see if there is DHCP request being sent when you do "dhclient"?  On the machine that is working - can you run wireshark and see if the DHCP request is being broadcast and if the AP is responding?

I forgot to mention that you should file a bug report on [Launchpad](https://bugs.launchpad.net).  Even if you get assistance through the forums there are users on Launchpad who may be able to assist you better than any of us.  You can also try #rt2x00 on freenode (please let me know if you don't know what that is) or you can usually find me in #ubuntu-us-ny.  #rt2x00 is a developers channel so I'm not sure how much they can help you with operation, but it's their driver so hopefully they'll help.  I've been in the channel asking if anyone can help with operational issues but haven't received any replies yet so hopefully they're all just at work at the moment.

Let me know if any of that helps.

---

