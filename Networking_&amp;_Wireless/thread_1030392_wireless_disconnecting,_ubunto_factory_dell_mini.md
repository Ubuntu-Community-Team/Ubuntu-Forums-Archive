---
title: "wireless disconnecting, ubunto factory dell mini"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by JRSinOK on 2009-01-04
Please help me trouble shoot this problem.  I am new to Ubuntu and am not sure where to turn.  I will post as much info as I can, it may not all be relevant.  

My system will start up and connect to the wireless router, but after some time (variable  1 min to 45 min) it quits working and won't re-connect.

Any idea?  I will include all of the output code I can

```
jimmy@jimmy:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
jimmy@jimmy:~$ 
```

```
jimmy@jimmy:~$  iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"stallings"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:6B:80:70:88   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
jimmy@jimmy:~$ lsmod
Module                  Size  Used by
wl                   1077012  0 
parport_pc             36260  0 
ppdev                  10372  0 
parport                37704  2 parport_pc,ppdev
uvcvideo               58116  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
dcdbas                  9504  0 
rfcomm                 41232  2 
l2cap                  25472  13 rfcomm
hci_usb                16412  2 
bluetooth              60772  7 rfcomm,l2cap,hci_usb
i915                   32512  2 
acpi_cpufreq           10796  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5156  0 
snd_seq_midi            9376  0 
snd_seq_oss            35328  0 
snd_seq_dummy           4868  0 
snd_pcm_oss            42144  0 
snd_hda_intel         344848  3 
snd_seq_midi_event      8320  2 snd_seq_midi,snd_seq_oss
snd_rawmidi            25632  1 snd_seq_midi
snd_hwdep              10500  1 snd_hda_intel
snd_pcm                78596  2 snd_pcm_oss,snd_hda_intel
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_mixer_oss          17792  1 snd_pcm_oss
snd_seq                53968  6 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
drm                    82196  3 i915
snd_seq_device          9484  5 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_rawmidi,snd_seq
snd                    56868  17 snd_seq_oss,snd_seq_dummy,snd_pcm_oss,snd_hda_intel,snd_rawmidi,snd_hwdep,snd_pcm,snd_mixer_oss,snd_seq,snd_timer,snd_seq_device
intel_agp              25364  1 
agpgart                34632  3 drm,intel_agp
soundcore               8800  1 snd
ndiswrapper           192280  0 
ieee80211_crypt_tkip    11520  0 
r8169                  33156  0 
ieee80211_crypt         6912  2 wl,ieee80211_crypt_tkip
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               7940  0 
psmouse                40336  0 
fuse                   50068  3 
ahci                   28420  0 
squashfs               48776  0 
unionfs                73168  0 
isofs                  35876  0 
zlib_inflate           18176  2 squashfs,isofs

```

```
jimmy@jimmy:~$ dmesg | grep "wlan0"
[   18.389440] wlan0: ethernet device 00:23:08:48:ed:77 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: '', 14E4:4315.5.conf
[   18.389744] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   26.194388] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.767885] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.662141] wlan0: no IPv6 routers present

```

```
jimmy@jimmy:~$ sudo lshw -C network
[sudo] password for jimmy: 
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:08:48:ed:77
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d5:95:d5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.104 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

```
jimmy@jimmy:~$ lsb_release -d
Description:	Ubuntu 8.04.1
```

```
jimmy@jimmy:~$ uname -mr
2.6.24-19-lpia i686
```

```
jimmy@jimmy:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.
```

also, here is the system log when things quit working

```
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jan  4 09:55:34 jimmy NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5621 
Jan  4 09:55:34 jimmy NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Missing link name TLV (errno = Invalid argument) 
Jan  4 09:55:34 jimmy avahi-daemon[4693]: Withdrawing address record for 192.168.1.101 on wlan0.
Jan  4 09:55:34 jimmy avahi-daemon[4693]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Jan  4 09:55:34 jimmy avahi-daemon[4693]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) starting connection 'Stallings' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0/wireless): connection 'Stallings' requires no security.  No secrets needed. 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: added 'ssid' value 'stallings' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:55:39 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:55:49 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Jan  4 09:55:49 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:55:53 jimmy ntpd[5720]: sendto(91.189.94.4) (fd=23): Invalid argument
Jan  4 09:55:54 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Jan  4 09:55:59 jimmy NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Activation (wlan0) failed for access point (stallings) 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Marking connection 'Stallings' invalid. 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Activation (wlan0) failed. 
Jan  4 09:55:59 jimmy NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jan  4 09:55:59 jimmy NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) starting connection 'Stallings' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0/wireless): connection 'Stallings' requires no security.  No secrets needed. 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: added 'ssid' value 'stallings' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  4 09:56:08 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:56:13 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:56:23 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Jan  4 09:56:23 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:56:28 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Jan  4 09:56:33 jimmy NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Activation (wlan0) failed for access point (stallings) 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Marking connection 'Stallings' invalid. 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Activation (wlan0) failed. 
Jan  4 09:56:33 jimmy NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jan  4 09:56:33 jimmy NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
```


Sorry for the long post, but i'm not sure what is needed.

---

### Post by JRSinOK on 2009-01-05
~Bump~

Anyone?  Dell customer support is horrible.  I sat on the phone for two hours yesterday only to be told that no was working who was familiar with Ubuntu. I could really use some guidance.

Thanks,
JRS

---

### Post by maggiagg on 2009-01-05
Hi there

I&#7743; having a similiar problem on my desktop. After restart the wireless network is running for random time (often 2-8hours) then it looses network connection. I  cannot ping anything. If I do :
sudo /etc/init.d/networking restart
then I&#7743; able to ping the router and useually nothing else (once I was able to ping outside of my local network).

I have tried
sudo /etc/init.d/dbus restart 
but it did not seem to affect anything. 

If I try iwconfig I can see that I have IP adresses and everything looks the same as when the network is working properly.

I&#7743; running 2 wireless cards on my computer (actually running as a server). Before updating to 8.10 everything worked flawlessly.

Regards

---

### Post by superprash2003 on 2009-01-05
does this happen to all wifi networks?? what error message do you get?

---

### Post by JRSinOK on 2009-01-05
My issue does happen with all wifi networks I have connected to.  Two with WEP and two without any securtity.  

I don't get an error, other than what I posted in the system logs, I just loose connection.

---

### Post by maggiagg on 2009-01-27
Hi 

I´m not getting any error message. 
-The browser is not connecting. 
-Apache is not accessible
-Samba is not accessible - ie shared folders are not accessible
-It´s not possible to ping or connect to the server on IP. The only way to access it is through the virtual server on the router - ie my internet adress is working.
-If I restart the server or restart the network service in ubuntu everything works for a while - then it stops working again.

---

