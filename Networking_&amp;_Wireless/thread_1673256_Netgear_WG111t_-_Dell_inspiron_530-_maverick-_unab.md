---
title: "Netgear WG111t - Dell inspiron 530- maverick- unable to connect to network"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Tedd81 on 2011-01-22
Hello All!

I am having trouble connecting to my home network, an Apple AirPort Extreme (UFO Type- NOT MY CHOICE!!).

I can 'see' my network in network manager but connection fails to obtain addresses or authenticate password. I have tried my password in both HEX and text (WPA2/PSK). 

Please Help!!!

Some information:

```
$ lsb_release -d
Description:	Ubuntu 10.10
```

```
$ uname -mr
2.6.35-22-generic i686
```

```
$ lsusb
Bus 001 Device 005: ID 1385:4250 Netgear, Inc WG111T
```

```
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:6c:37:70:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Extreme"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ lsmod
Module                  Size  Used by
ndiswrapper           184207  0 
```

```
$ dmesg | grep ndiswrapper
[   11.479083] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   11.981888] ndiswrapper: driver athfmwdl (,12/05/2003,1.00.001) loaded
[   12.117989] usbcore: registered new interface driver ndiswrapper
[   13.065573] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
```

```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:37:70:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwg11t driverversion=1.56+NETGEAR,01/07/2005,1.0.1.10 link=no multicast=yes wireless=IEEE 802.11g

```

```
$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:24:02:C9:4B
                    ESSID:"Extreme"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

```
$ sudo /etc/init.d/networking restart
/etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                               [ OK ]
```

If more info is needed please ask!!

Please. Please Help!!

Big thanks in advance!!

Ted

---

### Post by Tedd81 on 2011-01-23
bump...

Please!

---

### Post by Tedd81 on 2011-01-23
Hi all,

some more info:

I have tried with little joy:

[https://help.ubuntu.com/community/WifiDocs/Device/WG111T]("https://help.ubuntu.com/community/WifiDocs/Device/WG111T")

[http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/]("http://garethrwhite.wordpress.com/2009/02/05/netgear-wg111t-ubuntu/")

[http://ubuntuforums.org/showpost.php?p=2361840&postcount=9]("http://ubuntuforums.org/showpost.php?p=2361840&postcount=9")

[http://www.associatedcontent.com/article/2665279/how_to_install_and_use_a_wg111t_wireless.html?cat=15]("http://www.associatedcontent.com/article/2665279/how_to_install_and_use_a_wg111t_wireless.html?cat=15")

[http://ubuntuforums.org/showthread.php?t=549959]("http://ubuntuforums.org/showthread.php?t=549959")

here is my daemon.log

```
$ cat /var/log/daemon.log | grep NetworkManager
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0/wireless): connection 'Auto Extreme' has security, and secrets exist.  No new secrets needed.
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Config: added 'ssid' value 'Extreme'
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Config: added 'scan_ssid' value '1'
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Config: added 'psk' value '<omitted>'
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> Config: set interface ap_scan to 1
Jan 23 15:29:07 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 23 15:30:08 edwin-Inspiron-530 NetworkManager[972]: <warn> Activation (wlan0/wireless): association took too long.
Jan 23 15:30:08 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jan 23 15:30:08 edwin-Inspiron-530 NetworkManager[972]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan 23 15:30:08 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jan 23 15:30:10 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Jan 23 15:30:10 edwin-Inspiron-530 NetworkManager[972]: <warn> Activation (wlan0) failed for access point (Extreme)
Jan 23 15:30:10 edwin-Inspiron-530 NetworkManager[972]: <info> Marking connection 'Auto Extreme' invalid.
Jan 23 15:30:10 edwin-Inspiron-530 NetworkManager[972]: <warn> Activation (wlan0) failed.
Jan 23 15:30:10 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jan 23 15:30:10 edwin-Inspiron-530 NetworkManager[972]: <info> (wlan0): deactivating device (reason: 0).
```

I only included the last connection attempt as there would have been loads of text in this post.  I'm not sure what the log is telling me. 

Please, someone, cast some light on what the log is telling me!

Please help!

Thanks Ted

---

### Post by Tedd81 on 2011-01-23
Hi,

A more detailed daemon.log:

```

Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> NetworkManager (version 0.8.1) is starting...
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> trying to start the modem manager...
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: init!
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: update_system_hostname
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPluginIfupdown: management mode: unmanaged
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: end _init.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    Ifupdown: get unmanaged devices count: 0
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: (146598736) ... get_connections.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: (146598736) ... get_connections (managed=false): return empty list.
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]:    Ifupdown: get unmanaged devices count: 0
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> Networking is enabled by state file
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> modem-manager is now available
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 23 19:30:11 edwin-Inspiron-530 NetworkManager[999]: <info> Trying to start the supplicant...
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan0, iface: wlan0)
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <error> [1295811013.13007] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 2)
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): now managed
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): bringing up device.
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): preparing device.
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): deactivating device (reason: 2).
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant interface state:  starting -> ready
Jan 23 19:30:13 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jan 23 19:30:16 edwin-Inspiron-530 NetworkManager[999]: <error> [1295811016.727413] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan 23 19:30:16 edwin-Inspiron-530 NetworkManager[999]: <error> [1295811016.744101] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) starting connection 'Auto Extreme'
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0/wireless): access point 'Auto Extreme' has security, but secrets are required.
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0/wireless): connection 'Auto Extreme' has security, and secrets exist.  No new secrets needed.
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Config: added 'ssid' value 'Extreme'
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Config: added 'scan_ssid' value '1'
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Config: added 'psk' value '<omitted>'
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> Config: set interface ap_scan to 1
Jan 23 19:30:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jan 23 19:30:23 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 23 19:30:33 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 23 19:30:33 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 23 19:30:38 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 23 19:30:48 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 23 19:30:48 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 23 19:30:53 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 23 19:31:03 edwin-Inspiron-530 NetworkManager[999]: <warn> (wlan0): link timed out.
Jan 23 19:31:03 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 23 19:31:03 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 23 19:31:08 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 23 19:31:18 edwin-Inspiron-530 NetworkManager[999]: <warn> Activation (wlan0/wireless): association took too long.
Jan 23 19:31:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jan 23 19:31:18 edwin-Inspiron-530 NetworkManager[999]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan 23 19:31:18 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jan 23 19:31:20 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Jan 23 19:31:20 edwin-Inspiron-530 NetworkManager[999]: <warn> Activation (wlan0) failed for access point (Extreme)
Jan 23 19:31:20 edwin-Inspiron-530 NetworkManager[999]: <info> Marking connection 'Auto Extreme' invalid.
Jan 23 19:31:20 edwin-Inspiron-530 NetworkManager[999]: <warn> Activation (wlan0) failed.
Jan 23 19:31:20 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jan 23 19:31:20 edwin-Inspiron-530 NetworkManager[999]: <info> (wlan0): deactivating device (reason: 0).


```

thanks 

Ted

---

### Post by Tedd81 on 2011-01-23
Hi,

I thought that there might be a problem with wpasupplicant so I followed the manual config outlined here:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")

I tried to test the config with the following results:

```

$ wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
Line 2: failed to parse ssid 'Extreme'.
Line 2: failed to parse ssid 'Extreme'.
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Line 6: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout

```

help?!

One thing I noticed is the driver.
If I use -Dndiswrapper I get error saying driver not supported so I use -Dwext in the error???

What am I missing?

Ted

---

### Post by Truxx on 2011-01-23
What have u entered in wpa_supplicant.conf?

---

### Post by Tedd81 on 2011-01-24
Hi!

Truxx, thanks for your post!

Here is my wpa_supplicant.conf, key omitted.


```
network={
        ssid=Extreme
        proto=WPA
        key_mgmt=WPA-PSK
        psk="hex key"
  }
```

Any pointers gladly received!!

Thanks Ted

---

### Post by PCNetSpec on 2011-03-30
I know it's an old post, but for future readers..

Don't use ndiswrapper, there are Linux native drivers for the Netgear WG111T.

Instructions here:
[http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572](http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572)

---

