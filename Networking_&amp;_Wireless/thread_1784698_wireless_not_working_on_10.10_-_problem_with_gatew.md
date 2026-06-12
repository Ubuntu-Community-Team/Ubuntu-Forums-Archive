---
title: "wireless not working on 10.10 - problem with gateway ?"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by marieJJ on 2011-06-17
Hi,

I have installed 10.10 a few weeks ago and was able to have a wired internet connection without problems. However I haven' been able to get my wireless to work. 
Here are the commands I tried which might give a clue to what's wrong to someone helpful...
From reading other post, I think the gateway is missing but I am not able to set it up properly...


```

lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro NVS 140M] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1c:23:a1:1b:1b  
          inet6 addr: fe80::21c:23ff:fea1:1b1b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82213 (82.2 KB)  TX bytes:48423 (48.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11384 (11.3 KB)  TX bytes:11384 (11.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:d2:59:55  
          inet6 addr: fe80::21b:77ff:fed2:5955/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20719 (20.7 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:77:d2:59:55  
          inet addr:169.254.7.141  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

```

sudo dhclient

marielle@dell-Latitude-D830:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5748
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1c:23:a1:1b:1b
Sending on   LPF/eth0/00:1c:23:a1:1b:1b
Listening on LPF/wlan0/00:1b:77:d2:59:55
Sending on   LPF/wlan0/00:1b:77:d2:59:55
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
HCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```

sudo route add default gw 192.168.0.1

```

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1003   0        0 wlan0

```

```

cat /etc/ressolv.conf
# Generated by NetworkManager

```

---

### Post by chili555 on 2011-06-17
> marielle@dell-Latitude-D830:~$ sudo dhclientAs much as I admire old school command-line skill, you are unlikely to get manual methods working when Network Manager is installed and running, which it is by default in 10.10. How about we have a peek at:```
dmesg | grep iwl
rfkill list all
```

---

### Post by marieJJ on 2011-06-17
Thanks...here it goes

```

dmesg | grep iwl

[    9.466298] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    9.466301] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    9.466387] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.466409] iwl3945 0000:0c:00.0: setting latency timer to 64
[    9.527533] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    9.527537] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    9.527837] iwl3945 0000:0c:00.0: irq 46 for MSI/MSI-X
[    9.541940] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    9.983445] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[11470.796681] iwl3945 0000:0c:00.0: failed to remove IBSS station 00:00:00:00:00:00
[11478.298461] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[17524.368181] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload.
[17524.368195] iwl3945 0000:0c:00.0: On demand firmware reload

```

```

rfkill list all

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by marieJJ on 2011-06-20
Sorry but I am still lost here....

---

### Post by marieJJ on 2011-06-21
Out of desperation I was going to try to upgrade to 11.04. Is there less wireless problems with 11.04 ? Any views ?

---

### Post by dandnsmith on 2011-06-21
The number of posts for 11.04 with wireless problems seemd to be rising.

To me, as a wired connection user, it seems that 10.04 might be the best bet - a lot of the problems have been answered.

---

### Post by chili555 on 2011-06-21
> **marieJJ said:**
> Out of desperation I was going to try to upgrade to 11.04. Is there less wireless problems with 11.04 ? Any views ?Less than 10.10 for iwl3945? No. I say that because iwl3945 has worked perfectly for me since 8.something, including 10.10 and 11.04. I suspect this has something to do with your problem:> [17524.368181] iwl3945 0000:0c:00.0: queue 2 stuck 3 time. Fw reload.
[17524.368195] iwl3945 0000:0c:00.0: On demand firmware reloadLet's try a fix. Please do:```
sudo gedit /etc/modprobe.d/iwl3945.conf
```Add a single line:```
options iwl3945 fw_restart3945=1
```Proofread carefully, save and close gedit. Reboot and let us have your report. Are things better, worse or the same?```
dmesg | grep iwl
```

Sorry I lost track of your case; my sis and her hubby stopped by for a visit.

---

### Post by marieJJ on 2011-06-21
No problem....

created the conf file
I think things are the same

```

marielle@dell-Latitude-D830:/etc/modprobe.d$ more iwl3945.conf 
options iwl3945 fw_restart3945=1

```

```

marielle@dell-Latitude-D830:~$ dmesg | grep iwl
[   11.634252] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.634256] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   11.634328] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.634343] iwl3945 0000:0c:00.0: setting latency timer to 64
[   11.693704] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.693708] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.693967] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[   11.730075] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.355096] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9

```

---

### Post by chili555 on 2011-06-21
> I think things are the sameIn terms of being able to connect? You do not see the error is dmesg yet. Are there any clues here?```
sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25
```We are trying to see the last 25 instances of the driver, iwl3945 and Network Manager and 'network.'

---

### Post by marieJJ on 2011-06-21
```

marielle@dell-Latitude-D830:~$ sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25
[sudo] password for marielle: 
Jun 21 22:18:40 dell-Latitude-D830 kernel: [ 1078.112292] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:19:14 dell-Latitude-D830 kernel: [ 1112.036061] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:19:48 dell-Latitude-D830 kernel: [ 1146.080282] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:20:22 dell-Latitude-D830 kernel: [ 1180.064251] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:20:56 dell-Latitude-D830 kernel: [ 1214.048282] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:21:30 dell-Latitude-D830 kernel: [ 1248.096169] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:22:04 dell-Latitude-D830 kernel: [ 1282.016214] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:22:38 dell-Latitude-D830 kernel: [ 1316.065169] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:23:12 dell-Latitude-D830 kernel: [ 1350.049184] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:23:46 dell-Latitude-D830 kernel: [ 1384.032197] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:24:20 dell-Latitude-D830 kernel: [ 1418.080309] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:24:54 dell-Latitude-D830 kernel: [ 1452.000229] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:25:28 dell-Latitude-D830 kernel: [ 1486.048145] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:26:02 dell-Latitude-D830 kernel: [ 1520.096190] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:26:36 dell-Latitude-D830 kernel: [ 1554.016197] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:27:10 dell-Latitude-D830 kernel: [ 1588.064199] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:27:44 dell-Latitude-D830 kernel: [ 1622.048288] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:28:18 dell-Latitude-D830 kernel: [ 1656.032199] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:28:52 dell-Latitude-D830 kernel: [ 1690.080172] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:29:26 dell-Latitude-D830 kernel: [ 1724.064199] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:30:00 dell-Latitude-D830 kernel: [ 1758.048189] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:30:34 dell-Latitude-D830 kernel: [ 1792.096242] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:31:08 dell-Latitude-D830 kernel: [ 1826.016319] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:31:42 dell-Latitude-D830 kernel: [ 1860.064282] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Jun 21 22:32:16 dell-Latitude-D830 kernel: [ 1894.048151] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

```

---

### Post by chili555 on 2011-06-21
> Jun 21 22:32:16 dell-Latitude-D830 kernel: [ 1894.048151] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)Uh oh! IBSS is for ad-hoc or computer-to-computer connections. Did you Create New Wireless Network in Network Manager? That is a bit misleading; it actually means, "Establish New computer-to-computer connection; aka Internet Connection Sharing." Can you click the NM icon and check? Is that what you intended?

I didn't think so. If not, please delete, remove and expunge all those settings; yes, every one of them. Then do:```
sudo iwconfig wlan0 mode managed
```'Managed' means the wireless radio will be managed by the router or other access point; the router will set the channel, transmission speed, etc.

Then reboot and let NM do all the work for you; it should not be necessary to fill in any details.

If I am wrong in my assumptions, feel free to correct me.

---

### Post by marieJJ on 2011-06-22
Here is the settings I had :
Wireless mode : ad-hoc
I changed this to Infrastructure
IPv4 settings : Method : shared to other computers
I changed this to Disabled

Then did
```

sudo iwconfig wlan0 mode managed

```

reboot

Something definitely happens when I connect but I get disconnected almost immediately and the window with my encrypted password (I am using WEP) keeps popping up.

```

sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Activation (wlan0/wireless): connection 'Nusrat's Net' has security, and secrets exist.  No new secrets needed.
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: added 'ssid' value 'Nusrat's Net'
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: added 'scan_ssid' value '1'
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: added 'auth_alg' value 'OPEN'
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: added 'wep_key0' value '<omitted>'
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: added 'wep_tx_keyidx' value '0'
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> Config: set interface ap_scan to 1
Jun 22 21:16:46 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 21:16:48 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 22 21:16:58 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 22 21:16:58 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 21:17:01 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 22 21:17:11 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 22 21:17:11 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 21:17:14 dell-Latitude-D830 NetworkManager[946]: <info> (wlan0): supplicant connection state:  scanning -> associating

```

---

### Post by chili555 on 2011-06-22
> Wireless mode : ad-hoc
I changed this to InfrastructureYes, correct!> IPv4 settings : Method : shared to other computers
I changed this to Disabled
Oops! Nope, it needs to be Automatic (DHCP). Please change it and try again. My keyboard is buzzing; I think it means we're almost there!> added 'wep_key0' value '<omitted>'Once we get reliably connected, I suggest you change to WPA2-PSK. > nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failedThis looks scary but it pops up on my system and I connect instantly and stably. I think it's harmless.

---

### Post by marieJJ on 2011-06-22
IPv4 settings changed to Automatic (DHCP).
IPv6 settings is set to Ignore - I guess it's OK

After reboot, still no joy

```

 sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25

Jun 22 22:08:09 dell-Latitude-D830 NetworkManager[970]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 22 22:08:09 dell-Latitude-D830 NetworkManager[970]: <info> Config: set interface ap_scan to 1
Jun 22 22:08:09 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 22:08:10 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun 22 22:08:10 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 22:08:12 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 22 22:08:22 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 22 22:08:22 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 22:08:25 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 22 22:08:35 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 22 22:08:35 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 22:08:38 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 22 22:08:41 dell-Latitude-D830 NetworkManager[970]: <warn> (wlan0): link timed out.
Jun 22 22:08:48 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 22 22:08:48 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 22:08:58 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 22 22:09:08 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 22 22:09:08 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <warn> Activation (wlan0/wireless): association took too long.
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): device state change: 5 -> 9 (reason 7)
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <warn> Activation (wlan0) failed for access point (Nusrat's Net)
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <info> Marking connection 'Nusrat's Net' invalid.
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <warn> Activation (wlan0) failed.
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jun 22 22:09:10 dell-Latitude-D830 NetworkManager[970]: <info> (wlan0): deactivating device (reason: 0).

```

---

### Post by chili555 on 2011-06-22
Do you own the router or access point? I'm wondering if the system likes ESSIDs with spaces in the name. Is it feasible to change the name to NusratNet? How many characters in the WEP key? DON"T tell us the key; just how many characters. 12? 139? 4?

---

### Post by marieJJ on 2011-06-22
Yes, so it should be possible to change the ESSID's name but of course it will be a pain ...
It's a key with 25 characters.

---

### Post by chili555 on 2011-06-22
> It's a key with 25 characters.Hex WEP keys are allowed to have 10 or 2[COLOR="Red"]**6**[/COLOR] characters, ASCII are allowed 5 or 13. Would you please double-check?

[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)> A 128-bit WEP key is almost always entered by users as a string of [COLOR="Red"]26[/COLOR] hexadecimal (base 16) characters (0-9 and A-F). Each character represents four bits of the key. 26 digits of four bits each gives 104 bits; adding the 24-bit IV produces the final 128-bit WEP key.

---

### Post by marieJJ on 2011-06-22
<big sigh>OK, It is 26 characters and I made a mistake typing it...please be patient and don't pull your hair if you have any...
Still no connection

```

sudo cat /var/log/syslog | grep -e etwork -e iwl | tail -n25

Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Activation (wlan0/wireless): connection 'Nusrat's Net' has security, and secrets exist.  No new secrets needed.
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: added 'ssid' value 'Nusrat's Net'
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: added 'scan_ssid' value '1'
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: added 'auth_alg' value 'OPEN'
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: added 'wep_key0' value '<omitted>'
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: added 'wep_tx_keyidx' value '0'
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> Config: set interface ap_scan to 1
Jun 23 00:04:56 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 23 00:05:06 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 23 00:05:16 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 23 00:05:16 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 23 00:05:32 dell-Latitude-D830 NetworkManager[935]: <warn> (wlan0): link timed out.
Jun 23 00:05:49 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 23 00:05:56 dell-Latitude-D830 NetworkManager[935]: <warn> Activation (wlan0/wireless): association took too long.
Jun 23 00:05:56 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun 23 00:05:56 dell-Latitude-D830 NetworkManager[935]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun 23 00:05:56 dell-Latitude-D830 NetworkManager[935]: <info> (wlan0): supplicant connection state:  associating -> disconnected

```

---

### Post by chili555 on 2011-06-23
When I compare these syslogs with what you had in previous posts; i.e. continuous connect-disconnect, this actually looks pretty healthy...except it just won't take that last step and connect. I have a few suggestions. First, Click the Network Manager icon and Edit Coonections. Select Wireless and Wireless Security. Tick the box Show Password. Check and double-check the password. Try it with upper-case and lower-case letters, if any, in the key; e.g. 096ce... as well as 096CE...

You could also try removing security from the router temporarily to see if it connects, or, even better, move straight to WPA2-PSK.

We could also try the compat-wireless suite:  [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)  It's a bit more complex than point-and-click but not at all difficult.

Last, you could burn the live CD for Natty 11.04 and see if it works as expected.

I will be very happy to help in any way I can. I have plenty of hair remaining!

---

### Post by marieJJ on 2011-08-04
Finally upgraded to Natty but no joy.
Wireless connection works fine when I remove the password from the router but fails again when I put the security back on.
Any suggestions on what I can try next ?
Tx !

---

### Post by chili555 on 2011-08-04
> **marieJJ said:**
> Finally upgraded to Natty but no joy.
Wireless connection works fine when I remove the password from the router but fails again when I put the security back on.
Any suggestions on what I can try next ?
Tx !Have you tried with WPA or WPA2? Maybe WEP is the issue.

---

### Post by marieJJ on 2011-08-04
Yes, WPA worked !!
Thanks a lot, really appreciates the time you spent helping me.

---

