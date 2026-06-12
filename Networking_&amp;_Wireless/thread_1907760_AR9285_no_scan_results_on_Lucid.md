---
title: "AR9285 no scan results on Lucid"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by KV Salzgitter on 2012-01-12
Hallo,
i recently bought an Acer Aspire 5250 notebook and installed Kubuntu Lucid on it. Now i do have a problem with a wireless card Atheros AR9285. It is intergrated in the system (what i think) properly, but does not return any scan results with "sudo iwlist scan", where my other netbook returns 10 cells. As my assumption even is that there is a defect in the network card, i send the notebook back to the manufacturer but it returned with the hint there is no hardware but a software-problem. Still i don't trust that!
I've even tested it with Kubuntu 11.04 from disk - same result.
I'll attach the output of various command, where i can't see a problem. Perhaps someone could give me a hint where or how i can further verify if there is a Hard or soft problem - or even help me solve the probelm.

Many thanks in advance

salzgitter@gruenes-buero:/var/log$ uname -a
Linux gruenes-buero 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux

salzgitter@gruenes-buero:/var/log$ lspci -nn | grep Atheros
06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

salzgitter@gruenes-buero:/var/log$ lsmod | grep ath
ath9k                  67819  0 
ath9k_common            2551  1 ath9k
mac80211              225459  2 ath9k,ath9k_common
ath9k_hw              223661  2 ath9k,ath9k_common
ath                     8041  2 ath9k,ath9k_hw
cfg80211              144266  4 ath9k,ath9k_common,mac80211,ath
led_class               2864  1 ath9k

salzgitter@gruenes-buero:/var/log$ sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

salzgitter@gruenes-buero:/var/log$ sudo rfkill list 
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
salzgitter@gruenes-buero:/var/log$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:78:e2:5b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full ip=192.168.4.121 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:90200000-9023ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:d6:45:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:90100000-9010ffff

salzgitter@gruenes-buero:/var/log$ nm-tool
NetworkManager Tool
State: connected
- Device: eth0  [Icem] ---------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        B8:70:F4:78:E2:5B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.4.121
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.4.100

    DNS:             192.168.4.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        68:A3:C4:D6:45:BC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

salzgitter@gruenes-buero:/var/log$ sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results

---

### Post by chili555 on 2012-01-12
Network Manager gives preference to wired ethernet if it's available. Please detach the ethernet cable, give the system a few moments to notice the change in state and try again:```
sudo iwlist wlan0 scan
```If the results are the same, let's look for messages:```
dmesg | grep -e ath -e wlan
```Thanks.

---

### Post by KV Salzgitter on 2012-01-12
Thanks,
i'm out of office right now, will only be back on Monday. Then i'll give them a try.

---

### Post by KV Salzgitter on 2012-01-16
So, i'm back!

No scan results, even with eth0 unplugged.

salzgitter@gruenes-buero:/var/log$ dmesg | grep -e ath -e wlan
[    0.875768] device-mapper: multipath: version 1.1.0 loaded
[    0.875776] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.938776] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.938799] ath9k 0000:07:00.0: setting latency timer to 64
[   12.989185] ath: EEPROM regdomain: 0x65
[   12.989191] ath: EEPROM indicates we should expect a direct regpair map
[   12.989201] ath: Country alpha2 being used: 00
[   12.989206] ath: Regpair used: 0x65
[   13.164326] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.166090] Registered led device: ath9k-phy0::radio
[   13.166140] Registered led device: ath9k-phy0::assoc
[   13.166194] Registered led device: ath9k-phy0::tx
[   13.166239] Registered led device: ath9k-phy0::rx
[   13.426957] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Searched for the last message in the net, only results with hardware/software switches found (detected by rfkill) or firmware updates.

Any more ideas?
Thanks in advance

---

### Post by chili555 on 2012-01-16
Let's see what Network Manager is doing all this time:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by KV Salzgitter on 2012-01-16
Hallo,
i added the last 100 lines, as in the last 20 only eth0 actions have been logged.
For your understanding, at the place where i'm now i have to select the Networkmanager profil "Icem" (static IP) to get an internet connection.


salzgitter@gruenes-buero:/var/log$ sudo cat /var/log/syslog | grep etwork | tail -n100
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: init!
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.2/0000:06:00.0/net/eth0, iface: eth0)
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.2/0000:06:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: end _init.
Jan 16 14:59:44 gruenes-buero NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 16 14:59:44 gruenes-buero NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: (141467376) ... get_connections.
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: (141467376) ... get_connections (managed=false): return empty list.
Jan 16 14:59:44 gruenes-buero NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): carrier is OFF
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): new Ethernet device (driver: 'atl1c')
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): now managed
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): bringing up device.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): preparing device.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 16 14:59:44 gruenes-buero NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:15.2/0000:06:00.0/net/eth0
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  modem-manager is now available
Jan 16 14:59:44 gruenes-buero NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/net/wlan0, iface: wlan0)
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath9k')
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): now managed
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): bringing up device.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): preparing device.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 16 14:59:44 gruenes-buero NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  Trying to start the supplicant...
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  dhclient started with pid 987
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 16 14:59:46 gruenes-buero NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 987
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  Activation (eth0) failed.
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Jan 16 15:00:32 gruenes-buero NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) starting connection 'Icem'
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 16 15:03:51 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 16 15:03:52 gruenes-buero NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jan 16 15:03:52 gruenes-buero NetworkManager: <info>  Policy set 'Icem' (eth0) as default for routing and DNS.
Jan 16 15:03:52 gruenes-buero NetworkManager: <info>  Activation (eth0) successful, device activated.
Jan 16 15:03:52 gruenes-buero NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.

---

### Post by chili555 on 2012-01-16
That's a bit difficult to decipher. Let's try again. Detach the ethernet cable temporarily and try to connect with wireless. There is wireless available there, isn't there? Now do:```
sudo cat /var/log/syslog | grep wlan | tail -n20
```So far, I don't see anything that's alarming.

---

### Post by KV Salzgitter on 2012-01-16
Sorry, that isn't the problem - at least up to now.
The problem is that i can't see any network, not with iwlist, not with nm-tool and not in the network-manager, where i no from my netbook that there are ca. 10 cells available here.

---

### Post by KV Salzgitter on 2012-01-16
looks like the wlan entries only are from the startup sequence and have been in the chunk i send before:

salzgitter@gruenes-buero:/var/log$ sudo cat /var/log/syslog | grep wlan | tail -n20
Jan 16 14:57:40 gruenes-buero NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 16 14:57:40 gruenes-buero kernel: [   15.815284] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 16 14:57:40 gruenes-buero NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jan 16 14:57:40 gruenes-buero NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jan 16 14:57:40 gruenes-buero NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/net/wlan0, iface: wlan0)
Jan 16 14:59:44 gruenes-buero NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.3/0000:07:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath9k')
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): now managed
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): bringing up device.
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): preparing device.
Jan 16 14:59:44 gruenes-buero kernel: [   13.682716] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jan 16 14:59:44 gruenes-buero NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready

---

### Post by chili555 on 2012-01-16
Please try:```
sudo modprobe -r ath9k
lsmod | grep ath
```Make sure all the ath family have departed. If not, remove them as well with:```
sudo modprobe -r ath_whomever
```Now do:```
sudo modprobe ath9k nohwcrypt=1
sudo iwlist wlan0 scan
```If it works, we can write onw quick file to make it persistant.

---

### Post by KV Salzgitter on 2012-01-16
The 'lsmod | grep ath' output is in my first message, i've even tried to remove the ath9k mod and reattach it with the nohwcrypt=1 parameter, as i read it somewhere in a forum.
Didn't seem to help then.

However i'll try it again tomorrow, when i'm back in office

- Thanks

---

### Post by KV Salzgitter on 2012-01-17
As i thought:
'lsmod | grep ath' -> as in first message
after 'sudo modprobe -r ath9k' -> empty
after 'sudo modprobe ath9k nohwcrypt=1' -> as in first message

'ifconfig -a' after 'modprobe -r' -> wlan0 is gone
after 'modprobe ath9k ...' -> wlan0 exists again

'sudo iwlist wlan0 scan' -> no scan results

dosn't anyone know about some low-level diagnosis of the card, or some log-levels so i could trace the 'iwlist scan' command?

---

### Post by chili555 on 2012-01-17
> **KV Salzgitter said:**
> As i thought:
'lsmod | grep ath' -> as in first message
after 'sudo modprobe -r ath9k' -> empty
after 'sudo modprobe ath9k nohwcrypt=1' -> as in first message

'ifconfig -a' after 'modprobe -r' -> wlan0 is gone
after 'modprobe ath9k ...' -> wlan0 exists again

'sudo iwlist wlan0 scan' -> no scan results

dosn't anyone know about some low-level diagnosis of the card, or some log-levels so i could trace the 'iwlist scan' command?Yes. The low-level diagnostics are in dmesg:```
dmesg | grep ath9
```I'd try again:```
dmesg
```Note the time-stamp at the last line so we can see what happens after that. Next, do:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
dmesg | grep ath9
```Post the result and we'll troubleshoot.

---

### Post by KV Salzgitter on 2012-01-19
I just gave the notebook back to the manucaturer for repair. Hopefully this will help. Otherwise i'll come back to this thread and do the analytics you propose.

Many thanks.

---

### Post by chili555 on 2012-01-19
> **KV Salzgitter said:**
> I just gave the notebook back to the manucaturer for repair. Hopefully this will help. Otherwise i'll come back to this thread and do the analytics you propose.

Many thanks.I'll be glad to help.

---

### Post by KV Salzgitter on 2012-02-22
Just to clarify what was happening. It seems to be an antenna issue! I came across this by chance, when i started the laptop having a wireless router (to be configured) right on my desk - and i catched a signal with the wireless card!

So the laptop goes back to the manufacturer for the fouth time - happy end is near!

---

