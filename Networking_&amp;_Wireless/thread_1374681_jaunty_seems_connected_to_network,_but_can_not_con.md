---
title: "jaunty seems connected to network, but can not connect anywhere"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Cenko on 2010-01-07
I have a weird issue that I have not seen on any forum. My jaunty on DELL studio laptop seems connected to net, but I can not access any network service (ssh, firefox etc.). But when I connect a cable the cable lights blink as it should be and in wireless connection my wifi light blinks.

It was working 2 days ago without problem, and I have not done big changes recently.

I removed and reinstalled network-manager and network-manager-gnome. Nothing changed. 

I see a message in each restart as follows (when Openafs is starting). I can reproduce it with "/etc/init.d/openafs-client restart"
```
ADVISEADDR:error in specifying interfaces: no existing ip interfaces found
```

Below are information that I can give for any help

#lspci
```
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
```


#lshw -c network
```
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:c0:24:0e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.4 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:89:a4:39
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: de:18:b8:0a:b6:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

#ifup wlan0   (When I am connected)
```
ifup: interface wlan0 already configured
```


#/etc/init.d/networking restart
```
* Reconfiguring network interfaces...

```

#iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"RTA1025W-6D0207"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:6D:02:07
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:1234-5678-90   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level:-40 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


#ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:21:70:89:a4:39
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10722 (10.7 KB)  TX bytes:10722 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:c0:24:0e
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fec0:240e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27566 (27.5 KB)  TX bytes:64229 (64.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-C0-24-0E-34-30-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

#cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

Any ideas?
Cheers

---

### Post by suseendran.rengabashyam on 2010-01-07
Hi,
   	Looks like the IP address has not been assigned to your network interface eth0. Let me know if you have a DHCP server running in your network. If you don't have a DHCP server running, you could try to connect to your network services by manually assigning ip address to the interface. You can do this by using Network Manager.

---

### Post by Iowan on 2010-01-07
[Here]("http://ubuntuforums.org/showthread.php?t=1156441") is a problem/solution I had with Jaunty wired connection.

---

### Post by Cenko on 2010-01-07
I think I solved the problem. I'll first be sure, and then post the solution I did, then flag this "solved". Thanks to answers! You helped me find the problem :)

---

### Post by Cenko on 2010-01-08
I'm mistaken, its not completely solved! But at least wired part is solved. I can connect with a cable now. What I did was:

I tried :

#sudo dhclient
This was giving an error like "can't write on resolv.conf, permission denied". I tried 

#lsattr /etc/resolv.conf 
and saw that file had attributes a and i. I removed them with 

#sudo chattr -ai /etc/resolv.conf
Then I was able to connect to wired network after running "dhclient"

And I was able to connect a open wireless network in my school (no password) . When I came home and tried to connect to wireless, I'm not able to again. This time it is a protected network (asks password), tried to connect but it asks password again and again. after trying to connect for a while.

Here is output of /var/log/syslog while I'm trying to connect my wireless network at home: (A bit long :D)

```

Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto RTA1025W-6D0207'
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 3 -> 4
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 4 -> 5
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto RTA1025W-6D0207' has security, but secrets are required.
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 5 -> 6
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 6 -> 4
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 4 -> 5
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto RTA1025W-6D0207' has security, and secrets exist.  No new secrets needed.
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: added 'ssid' value 'RTA1025W-6D0207'
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'

Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jan  8 19:44:42 PCCAST3891 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  8 19:44:42 PCCAST3891 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  Config: set interface ap_scan to 1
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan  8 19:44:42 PCCAST3891 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 19:44:43 PCCAST3891 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan  8 19:44:43 PCCAST3891 kernel: [12688.719019] wlan0: authenticate with AP 00:16:e3:6d:02:07
Jan  8 19:44:43 PCCAST3891 kernel: [12688.719888] wlan0: authenticate with AP 00:16:e3:6d:02:07
Jan  8 19:44:43 PCCAST3891 kernel: [12688.721687] wlan0: authenticated
Jan  8 19:44:43 PCCAST3891 kernel: [12688.721696] wlan0: associate with AP 00:16:e3:6d:02:07
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'RTA1025W-6D0207'.
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 5 -> 7
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction.
Jan  8 19:44:44 PCCAST3891 kernel: [12688.726329] wlan0: RX AssocResp from 00:16:e3:6d:02:07 (capab=0x411 status=0 aid=1)
Jan  8 19:44:44 PCCAST3891 kernel: [12688.726336] wlan0: associated
Jan  8 19:44:44 PCCAST3891 kernel: [12688.727270] iwlagn: Microcode SW error detected.  Restarting 0x82000000.
Jan  8 19:44:44 PCCAST3891 kernel: [12688.727299] iwlagn: Error setting new RXON (-5)
Jan  8 19:44:44 PCCAST3891 dhclient: Internet Systems Consortium DHCP Client V3.1.1
Jan  8 19:44:44 PCCAST3891 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  8 19:44:44 PCCAST3891 dhclient: All rights reserved.
Jan  8 19:44:44 PCCAST3891 dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan  8 19:44:44 PCCAST3891 dhclient:
Jan  8 19:44:44 PCCAST3891 dhclient: wmaster0: unknown hardware address type 801
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  dhclient started with pid 28016
Jan  8 19:44:44 PCCAST3891 dhclient: wmaster0: unknown hardware address type 801
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan  8 19:44:44 PCCAST3891 NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Jan  8 19:44:44 PCCAST3891 dhclient: Listening on LPF/wlan0/00:21:5d:c0:24:0e
Jan  8 19:44:44 PCCAST3891 dhclient: Sending on   LPF/wlan0/00:21:5d:c0:24:0e
Jan  8 19:44:44 PCCAST3891 dhclient: Sending on   Socket/fallback
Jan  8 19:44:44 PCCAST3891 kernel: [12688.783218] Registered led device: iwl-phy0:radio
Jan  8 19:44:44 PCCAST3891 kernel: [12688.783265] Registered led device: iwl-phy0:assoc
Jan  8 19:44:44 PCCAST3891 kernel: [12688.783302] Registered led device: iwl-phy0:RX
Jan  8 19:44:44 PCCAST3891 kernel: [12688.783341] Registered led device: iwl-phy0:TX
Jan  8 19:44:45 PCCAST3891 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jan  8 19:44:49 PCCAST3891 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jan  8 19:44:57 PCCAST3891 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jan  8 19:45:07 PCCAST3891 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jan  8 19:45:23 PCCAST3891 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it.
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 28016
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started...
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'Auto RTA1025W-6D0207'.
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 7 -> 6
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan  8 19:45:29 PCCAST3891 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete.
Jan  8 19:46:19 PCCAST3891 NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1539 (get_secrets_dialog_response_cb): canceled.
Jan  8 19:46:19 PCCAST3891 NetworkManager: <info>  (wlan0): device state change: 6 -> 9
Jan  8 19:46:19 PCCAST3891 NetworkManager: <info>  Activation (wlan0) failed for access point (RTA1025W-6D0207)
Jan  8 19:46:19 PCCAST3891 NetworkManager: <info>  Marking connection 'Auto RTA1025W-6D0207' invalid.
Jan  8 19:46:19 PCCAST3891 NetworkManager: <info>  Activation (wlan0) failed.

```

So I can connect to a network which has no pass, but not to my home network which has a pass.

When the password window comes up saying "Authentication required by wireless network", it indicates wireless security "WEP 40/128-bit Key", and authentication: "open system". These are automaticly detected right?

I read some stuff and it seems some people solved these issues with installing "linux-backports-modules-jaunty". Maybe I'll try that.

---

### Post by Cenko on 2010-01-08
SOLVED!

The following line solved my wireless problem too. 

```
sudo apt-get install linux-backports-modules-jaunty
```

Thanks for all help.

---

