---
title: "wifi problem thinkpad t30/r30"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by Antarctica32 on 2011-09-21
I feel like such a noob asking this but, I can't get my wifi to work on my thinkpad t30. I found it in the trash a while back and it didn't have a wifi pci card in it. I found out latter on that it used to be owned by a bank so they took out all the wifi cards in all the computers for security. well anyway, my teacher gave me his old r30 thinkpad which does have a pci wifi card. I took it out and put it in mine with no succes. I am able to see all the networks but can't join them. I think it is a problem with my driver, which I tried to blacklist but for some reason keeps staying as my driver?????? I am really confused and just want it to work now. ```
root@Turing2:~# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
root@Turing2:~# 

```

```
root@Turing2:~# sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 01
       serial: 00:20:e0:89:9d:25
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.3 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:f8000000-f8000fff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:0d:60:3b:26:12
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:d0200000-d0200fff ioport:8000(size=64)
root@Turing2:~# 

```

All help of any kind is greatly appreciated, as I have little clue what I am doing... Ok, maybe a more than a little

---

### Post by chili555 on 2011-09-21
> I think it is a problem with my driver, which I tried to blacklist but for some reason keeps staying as my driver?????? Why did you try to blacklist the driver? There are sometimes conflicting drivers, hostap for example, and, if you tried to get it going, ndiswrapper. What is in your blacklist file? What is loaded now?```
lsmod | grep -e orin -e host -e ndis
```Does your card support WPA ***and*** WPA2?```
sudo iwlist eth1 auth
```

---

### Post by Antarctica32 on 2011-09-22
Well I read somewhere that there could be 2 conflicting drivers, and that someone had fixed it by blacklisting it, this orinoco thing. Well anyway,
```
administrator@Turing2:~$ lsmod | grep -e orin -e host -e ndis
hostap_pci             44617  0 
hostap                 99846  1 hostap_pci
lib80211                5046  2 hostap_pci,hostap
orinoco_pci             2655  0 
orinoco                62842  1 orinoco_pci
cfg80211              126144  1 orinoco

```

and 
```
administrator@Turing2:~$ sudo iwlist eth1 auth
eth1      unknown authentication information.

```

well that sucks

thanks a lot for all the help even if it won't work.

---

### Post by chili555 on 2011-09-22
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two lines, if not already there:```
blacklist orinoco
blacklist orinoco_pci
```Proofread, save and close gedit. Reboot and let us have a progress report.

---

### Post by Antarctica32 on 2011-09-22
yeah I already had blacklist orinoco but not blacklist orinoco_pci, just added it. Now I am going to reboot.

---

### Post by Antarctica32 on 2011-09-22
same as before

---

### Post by chili555 on 2011-09-23
What happens when you try to join a network? Are you challenged for an encryption key? Any interesting clues here?```
dmesg | grep host
sudo cat /var/log/syslog | grep -e etwork -e host
```Thanks.

Not all Prism 2.5s do WPA and WPA2.

---

### Post by Antarctica32 on 2011-09-23
```

administrator@Turing2:~$ dmesg | grep host
[   29.244334] hostap_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   29.245961] hostap_pci: Registered netdevice wifi0
[   60.629762] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
]
```
then
```
Sep 22 21:45:56 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:45:56 Turing2 kernel: [ 3410.232172] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:45:56 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:45:56 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:45:59 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:00 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:00 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:00 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:01 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:01 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:01 Turing2 kernel: [ 3415.494517] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:01 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:01 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2417
Sep 22 21:46:04 Turing2 NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Red Leader'
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Red Leader' has security, and secrets exist.  No new secrets needed.
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Config: added 'ssid' value 'Red Leader'
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Sep 22 21:46:04 Turing2 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 22 21:46:04 Turing2 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 22 21:46:04 Turing2 NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Sep 22 21:46:04 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Sep 22 21:46:05 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Red Leader'.
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 22 21:46:05 Turing2 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Sep 22 21:46:05 Turing2 NetworkManager: <info>  dhclient started with pid 2480
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Sep 22 21:46:05 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep 22 21:46:05 Turing2 NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Sep 22 21:46:05 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:05 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:05 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Sep 22 21:46:05 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:06 Turing2 NetworkManager: <info>  wlan1: link timed out.
Sep 22 21:46:07 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:07 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:07 Turing2 kernel: [ 3421.113080] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:07 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:07 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:10 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:11 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:11 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:11 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:12 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:12 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:12 Turing2 kernel: [ 3426.447742] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:12 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:12 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:16 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:16 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:16 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:16 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:18 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:18 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:18 Turing2 kernel: [ 3431.962853] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:18 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:18 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:21 Turing2 NetworkManager: <info>  wlan0: link timed out.
Sep 22 21:46:21 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:21 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:21 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:22 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:23 Turing2 NetworkManager: <info>  wlan1: link timed out.
Sep 22 21:46:23 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:23 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:23 Turing2 kernel: [ 3437.207605] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:23 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:23 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:26 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:27 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:27 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:27 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:29 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:29 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:29 Turing2 kernel: [ 3442.722834] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:29 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:29 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:32 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:32 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:32 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:32 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:36 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:36 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:36 Turing2 kernel: [ 3449.703359] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:36 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:36 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Sep 22 21:46:37 Turing2 NetworkManager: <info>  wlan0: link timed out.
Sep 22 21:46:37 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:38 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:38 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:38 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:39 Turing2 NetworkManager: <info>  wlan1: link timed out.
Sep 22 21:46:43 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 22 21:46:43 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:44 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associated
Sep 22 21:46:44 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:44 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:46:44 Turing2 kernel: [ 3458.456891] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:44 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Sep 22 21:46:48 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:49 Turing2 NetworkManager: <info>  Activation (wlan1/wireless): association took too long.
Sep 22 21:46:49 Turing2 NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Sep 22 21:46:49 Turing2 NetworkManager: <info>  Activation (wlan1/wireless): asking for new secrets
Sep 22 21:46:49 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> disconnected
Sep 22 21:46:49 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Sep 22 21:46:49 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2480
Sep 22 21:46:50 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Sep 22 21:46:50 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan0): device state change: 7 -> 9 (reason 5)
Sep 22 21:46:50 Turing2 NetworkManager: <info>  Activation (wlan0) failed for access point (Red Leader)
Sep 22 21:46:50 Turing2 NetworkManager: <info>  Marking connection 'Auto Red Leader' invalid.
Sep 22 21:46:50 Turing2 NetworkManager: <info>  Activation (wlan0) failed.
Sep 22 21:46:50 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> associated
Sep 22 21:46:50 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:50 Turing2 wpa_supplicant[793]: No network configuration found for the current AP
Sep 22 21:46:50 Turing2 kernel: [ 3464.608857] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 22 21:46:50 Turing2 NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> disconnected
Sep 22 21:47:04 Turing2 NetworkManager: <info>  wlan1: link timed out.
Sep 23 15:01:57 Turing2 kernel: [    1.871223] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
Sep 23 15:01:57 Turing2 kernel: [   28.687711] type=1505 audit(1316804516.792:3):  operation="profile_load" pid=521 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 23 15:01:57 Turing2 kernel: [   29.244334] hostap_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Sep 23 15:01:57 Turing2 kernel: [   29.245961] hostap_pci: Registered netdevice wifi0
Sep 23 15:01:57 Turing2 NetworkManager: <info>  starting...
Sep 23 15:01:57 Turing2 avahi-daemon[607]: Network interface enumeration completed.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  Trying to start the modem-manager...
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: init!
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Sep 23 15:01:57 Turing2 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wifi0, iface: wifi0)
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wifi0, iface: wifi0): no ifupdown configuration found.
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0, iface: eth0)
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/irda0, iface: irda0)
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/irda0, iface: irda0): no ifupdown configuration found.
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: end _init.
Sep 23 15:01:57 Turing2 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 23 15:01:57 Turing2 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Sep 23 15:01:57 Turing2 NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: (157365488) ... get_connections.
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: (157365488) ... get_connections (managed=false): return empty list.
Sep 23 15:01:57 Turing2 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'hostap_pci')
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): now managed
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): bringing up device.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): preparing device.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Sep 23 15:01:57 Turing2 NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): carrier is OFF
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): now managed
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): bringing up device.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): preparing device.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0)
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wifi0, iface: wifi0)
Sep 23 15:01:57 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/net/wifi0, iface: wifi0): no ifupdown configuration found.
Sep 23 15:01:57 Turing2 NetworkManager: <info>  modem-manager is now available
Sep 23 15:01:57 Turing2 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep 23 15:01:57 Turing2 NetworkManager: <info>  Trying to start the supplicant...
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Sep 23 15:01:57 Turing2 NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Sep 23 15:01:58 Turing2 NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Sep 23 15:01:58 Turing2 NetworkManager: <info>  Found wlan radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Sep 23 15:01:59 Turing2 kernel: [   31.201940] type=1505 audit(1316804519.308:7):  operation="profile_replace" pid=950 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto Red Leader'
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto Red Leader' has security, but secrets are required.
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto Red Leader' has security, and secrets exist.  No new secrets needed.
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: added 'ssid' value 'Red Leader'
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Sep 23 15:02:27 Turing2 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 23 15:02:27 Turing2 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Sep 23 15:02:27 Turing2 NetworkManager: <info>  Config: set interface ap_scan to 1
Sep 23 15:02:27 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Sep 23 15:02:28 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Sep 23 15:02:28 Turing2 kernel: [   60.629762] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
Sep 23 15:02:29 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Sep 23 15:02:29 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Red Leader'.
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 23 15:02:29 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 23 15:02:29 Turing2 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Sep 23 15:02:29 Turing2 NetworkManager: <info>  dhclient started with pid 1477
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 23 15:02:29 Turing2 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Sep 23 15:02:29 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep 23 15:02:29 Turing2 NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Sep 23 15:02:46 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/net/wlan1, iface: wlan1)
Sep 23 15:02:46 Turing2 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Sep 23 15:02:46 Turing2 NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/net/wlan1_rename, iface: wlan1_rename)
Sep 23 15:02:46 Turing2 NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/ieee80211/phy0/rfkill0 disappeared
Sep 23 15:03:15 Turing2 NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.
Sep 23 15:03:15 Turing2 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 1477
Sep 23 15:03:15 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Sep 23 15:03:15 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Sep 23 15:03:15 Turing2 NetworkManager: <info>  Activation (wlan0/wireless): could not get IP configuration for connection 'Auto Red Leader'.
Sep 23 15:03:15 Turing2 NetworkManager: <info>  (wlan0): device state change: 7 -> 6 (reason 0)
Sep 23 15:03:15 Turing2 NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Sep 23 15:03:15 Turing2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Sep 23 15:03:37 Turing2 NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Sep 23 15:03:37 Turing2 NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Sep 23 15:03:37 Turing2 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep 23 15:03:37 Turing2 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep 23 15:03:37 Turing2 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Sep 23 15:03:37 Turing2 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Sep 23 15:03:38 Turing2 NetworkManager: <info>  dhclient started with pid 1684
Sep 23 15:03:38 Turing2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Sep 23 15:03:38 Turing2 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep 23 15:03:38 Turing2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Sep 23 15:03:38 Turing2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Sep 23 15:03:38 Turing2 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Sep 23 15:03:41 Turing2 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Sep 23 15:03:41 Turing2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 23 15:03:41 Turing2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 23 15:03:41 Turing2 NetworkManager: <info>    address 192.168.1.100
Sep 23 15:03:41 Turing2 NetworkManager: <info>    prefix 24 (255.255.255.0)
Sep 23 15:03:41 Turing2 NetworkManager: <info>    gateway 192.168.1.1
Sep 23 15:03:41 Turing2 NetworkManager: <info>    nameserver '68.87.64.150'
Sep 23 15:03:41 Turing2 NetworkManager: <info>    nameserver '68.87.75.198'
Sep 23 15:03:41 Turing2 NetworkManager: <info>    nameserver '192.168.1.1'
Sep 23 15:03:41 Turing2 NetworkManager: <info>    domain name 'hsd1.pa.comcast.net.'
Sep 23 15:03:41 Turing2 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 23 15:03:41 Turing2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 23 15:03:41 Turing2 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep 23 15:03:42 Turing2 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Sep 23 15:03:42 Turing2 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Sep 23 15:03:42 Turing2 NetworkManager: <info>  Activation (eth0) successful, device activated.
Sep 23 15:03:42 Turing2 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
```

After I log on it takes about 20 seconds untill it prompts for my network's password. I enter the password but nothing happens and it never says I am connected. Here is a screen shot of the pswd prompt. Usually (compared to other laptops I have used) where it says WEP and WEP2 it says WEP 128-bit passphrase. But the drop down box lets me choose from LEAP, WEP 40/128-passphrase, and Dynamic WEP (802.1X. Does this mean it can't do WEP and WEP 2?

---

### Post by Antarctica32 on 2011-09-23
ok, I am leaving now for the weekend and probably won't be able to post at all.

---

### Post by chili555 on 2011-09-23
I will see you when you return.

I imagine Network Manager would be a whole lot happier if it were not trying to juggle *THREE* interfaces, eth0, wlan0 and wlan1! Which is the Prism2.5? Please detach the ethernet cable before you proceed.

Yikes.

---

