---
title: "Wifi Problems in Ubuntu 10.10"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by goingnowherefast on 2011-04-28
Hello everyone. I have been an Ubuntu user for a year or so. My level is still ultra n00b but I am trying. Whenever I update Ubuntu there is always a WiFi problem, always. So now I am having problems getting wifi to work in 10.10. In Network Manager I can view wifi networks fine but I cannot connect. I tried with wicd also but I got as far as "getting ip" and then it would hang up. 

lspci
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

```iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"UYVTCS"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

mon0      IEEE 802.11abg  Mode:Monitor  Frequency:2.442 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

rfkill list
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I am not sure what driver I am using as I don't know how to exactly ID my driver. I know there is a way to ID the driver using airodump-ng but I have yet to find it. 

I have a feeling this is a driver issue as one time I was able to establish a connection that then dropped a few minutes later. I have a feeling I should be disabling/removing the current driver and replacing it with ipw3945 or possibly a driver ndiswrapped? The problem is I cannot figure out how to remove the current driver. 

I was going to switch back to 9.04 but I thought I would try to manually figure this one out instead of taking the easy way. If anyone could lend a hand it'd be greatly appreciated.

---

### Post by goingnowherefast on 2011-04-28
grep -i networkman /var/log/syslog
```

Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto UYVTCS' requires no security.  No secrets needed.
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Config: added 'ssid' value 'UYVTCS'
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Apr 28 14:43:12 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 14:43:14 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 14:43:19 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 28 14:43:19 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 14:43:21 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 14:43:26 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 28 14:43:26 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 14:43:27 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 14:43:27 comp-laptop NetworkManager: <info>  wlan0: link timed out.
Apr 28 14:43:32 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 28 14:43:32 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 14:43:34 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 14:43:39 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 28 14:43:39 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 14:43:41 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 14:43:43 comp-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 3 (reason 39)
Apr 28 14:43:43 comp-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 39).
Apr 28 14:43:43 comp-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 28 14:50:51 comp-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Apr 28 14:50:53 comp-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Apr 28 14:52:04 comp-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Apr 28 14:52:05 comp-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Apr 28 14:52:38 comp-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Apr 28 14:52:40 comp-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 8)
Apr 28 17:52:06 comp-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Apr 28 17:52:10 comp-laptop NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
Apr 28 17:52:10 comp-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
Apr 28 17:52:10 comp-laptop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2256
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  dhclient started with pid 7062
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 28 18:02:24 comp-laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Apr 28 18:02:28 comp-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Apr 28 18:02:29 comp-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Apr 28 18:02:40 comp-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
Apr 28 18:02:42 comp-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
Apr 28 18:02:56 comp-laptop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 28 18:02:56 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 28 18:02:56 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 28 18:02:56 comp-laptop NetworkManager: <info>    address 192.168.1.36
Apr 28 18:02:56 comp-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Apr 28 18:02:56 comp-laptop NetworkManager: <info>    gateway 192.168.1.1
Apr 28 18:02:56 comp-laptop NetworkManager: <info>    nameserver '200.48.225.130'
Apr 28 18:02:56 comp-laptop NetworkManager: <info>    nameserver '200.48.225.146'
Apr 28 18:02:56 comp-laptop NetworkManager: <info>    domain name 'domain.name'
Apr 28 18:02:56 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 28 18:02:56 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 28 18:02:56 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 28 18:02:57 comp-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 28 18:02:57 comp-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 28 18:02:57 comp-laptop NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 28 18:02:57 comp-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto UYVTCS'
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto UYVTCS' requires no security.  No secrets needed.
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Config: added 'ssid' value 'UYVTCS'
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Apr 28 19:21:01 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 19:21:03 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 19:21:08 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 28 19:21:08 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 19:21:10 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 19:21:15 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 28 19:21:15 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 28 19:21:16 comp-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 28 19:21:16 comp-laptop NetworkManager: <info>  wlan0: link timed out.

```

---

### Post by goingnowherefast on 2011-04-28
After a lot of trial and error the last thing I can try is blacklisting the current driver (iwl3945) , then using modprobe to remove the module, then install the win driver with ndiswrapper. Can someone please explain to me how to do that?!

---

