---
title: "WEP connection issue"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Doodaad on 2011-10-02
Hello all,
I am having an issue connecting to a 64 bit WEP wireless AP. When I try to connect it keeps asking for the WEP Key. I have read through the forums and most of the posts say to switch to WPA but I do not have that option as I don't own the router. Here are some code outputs that I picked up from other posts. Sorry for the copy/paste in advance I have to swap back and forth with windoze to post :p I also have an old Dell laptop that has the same issue I have double triple checked the WEP Key. [Edit] Scratch that the laptop does connect i just had to go outside and let it connect.(the ap is kinda far away) But my desktop is using an external antenna and is at full strength. I am thinking it may be an issue with how linux sends the key. I have even tried putting a 0x in front of the key (fedora fix) with no luck. Since my laptop will connect now i will share it and see if i can run some updates....

 I have an Edimax 7128g card which uses RT2561/RT61 chipset.

uname -mr 
2.6.38-8-generic x86_64 (Kubuntu)

lsb_release -d
Description:    Ubuntu Natty (development branch)

lspci
04:06.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI

5:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Greeley RV Park"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
ifconfig

eth0      Link encap:Ethernet  HWaddr 48:5b:39:36:d6:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2160 (2.1 KB)  TX bytes:2160 (2.1 KB)
lsmod

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:64:8a:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
337.210443] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
[  337.214656] wlan0: authenticated
[  337.214793] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
[  337.410139] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
[  337.411559] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)

shw -C network
*-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:64:8a:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fe8f8000-fe8fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 48:5b:39:36:d6:4b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fe9e0000-fe9fffff

iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:10:E7:B5:8B:83
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Greeley RV Park"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000015b71a675a
                    Extra: Last beacon: 11970ms ago
                    IE: Unknown: 000F477265656C6579205256205061726B
                    IE: Unknown: 010482840B16
                    IE: Unknown: 030108

sudo /etc/init.d/networking restart

* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...   

        sudo tail -n100 /var/log/syslog

Oct  2 18:10:51 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:10:52 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:10:52 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:10:52 ubuntu kernel: [ 2332.180369] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:10:52 ubuntu kernel: [ 2332.182587] wlan0: authenticated
Oct  2 18:10:52 ubuntu kernel: [ 2332.182723] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:10:53 ubuntu kernel: [ 2332.380063] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:10:53 ubuntu kernel: [ 2332.381487] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:10:54 ubuntu NetworkManager[948]: <warn> Activation (wlan0/wireless): association took too long.
Oct  2 18:10:54 ubuntu NetworkManager[948]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Oct  2 18:10:54 ubuntu NetworkManager[948]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct  2 18:10:54 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:11:05 ubuntu NetworkManager[948]: <warn> Failed to update connection secrets: 1 802-1x
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0/wireless): connection 'Greeley RV Park' has security, and secrets exist.  No new secrets needed.
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'ssid' value 'Greeley RV Park'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'scan_ssid' value '1'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'key_mgmt' value 'NONE'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'wep_key0' value '<omitted>'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'wep_key1' value '<omitted>'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'wep_key2' value '<omitted>'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'wep_key3' value '<omitted>'
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: added 'wep_tx_keyidx' value '0'
Oct  2 18:11:05 ubuntu NetworkManager[948]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  2 18:11:05 ubuntu NetworkManager[948]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> Config: set interface ap_scan to 1
Oct  2 18:11:05 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:11:06 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:11:06 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:11:06 ubuntu kernel: [ 2346.080244] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:06 ubuntu kernel: [ 2346.082469] wlan0: authenticated
Oct  2 18:11:06 ubuntu kernel: [ 2346.082508] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:07 ubuntu kernel: [ 2346.280066] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:11:07 ubuntu kernel: [ 2346.480079] wlan0: associate with 00:10:e7:b5:8b:83 (try 3)
Oct  2 18:11:07 ubuntu kernel: [ 2346.483819] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:11:16 ubuntu wpa_supplicant[1121]: Authentication with 00:10:e7:b5:8b:83 timed out.
Oct  2 18:11:16 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:11:16 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:11:18 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:11:18 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:11:18 ubuntu kernel: [ 2357.450419] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:18 ubuntu kernel: [ 2357.452662] wlan0: authenticated
Oct  2 18:11:18 ubuntu kernel: [ 2357.452796] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:18 ubuntu kernel: [ 2357.650140] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:11:18 ubuntu kernel: [ 2357.651564] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:11:28 ubuntu wpa_supplicant[1121]: Authentication with 00:10:e7:b5:8b:83 timed out.
Oct  2 18:11:28 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:11:28 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:11:29 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:11:29 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:11:29 ubuntu kernel: [ 2368.800316] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:29 ubuntu kernel: [ 2369.000139] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:11:29 ubuntu kernel: [ 2369.002442] wlan0: authenticated
Oct  2 18:11:29 ubuntu kernel: [ 2369.002579] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:30 ubuntu kernel: [ 2369.200139] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:11:30 ubuntu kernel: [ 2369.400137] wlan0: associate with 00:10:e7:b5:8b:83 (try 3)
Oct  2 18:11:30 ubuntu kernel: [ 2369.401572] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:11:39 ubuntu wpa_supplicant[1121]: Authentication with 00:10:e7:b5:8b:83 timed out.
Oct  2 18:11:39 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:11:39 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:11:40 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:11:40 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:11:40 ubuntu kernel: [ 2380.170403] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:40 ubuntu kernel: [ 2380.174070] wlan0: authenticated
Oct  2 18:11:40 ubuntu kernel: [ 2380.174113] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:41 ubuntu kernel: [ 2380.370135] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:11:41 ubuntu kernel: [ 2380.371570] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:11:46 ubuntu NetworkManager[948]: <warn> (wlan0): link timed out.
Oct  2 18:11:50 ubuntu wpa_supplicant[1121]: Authentication with 00:10:e7:b5:8b:83 timed out.
Oct  2 18:11:50 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:11:50 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:11:52 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:11:52 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:11:52 ubuntu kernel: [ 2391.520273] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:52 ubuntu kernel: [ 2391.524905] wlan0: authenticated
Oct  2 18:11:52 ubuntu kernel: [ 2391.525040] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:11:52 ubuntu kernel: [ 2391.720137] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:11:52 ubuntu kernel: [ 2391.721553] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:12:02 ubuntu wpa_supplicant[1121]: Authentication with 00:10:e7:b5:8b:83 timed out.
Oct  2 18:12:02 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:12:02 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct  2 18:12:03 ubuntu wpa_supplicant[1121]: Trying to associate with 00:10:e7:b5:8b:83 (SSID='Greeley RV Park' freq=2447 MHz)
Oct  2 18:12:03 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct  2 18:12:03 ubuntu kernel: [ 2402.870401] wlan0: authenticate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:12:03 ubuntu kernel: [ 2402.872701] wlan0: authenticated
Oct  2 18:12:03 ubuntu kernel: [ 2402.872875] wlan0: associate with 00:10:e7:b5:8b:83 (try 1)
Oct  2 18:12:03 ubuntu kernel: [ 2403.070133] wlan0: associate with 00:10:e7:b5:8b:83 (try 2)
Oct  2 18:12:03 ubuntu kernel: [ 2403.071560] wlan0: deauthenticated from 00:10:e7:b5:8b:83 (Reason: 9)
Oct  2 18:12:05 ubuntu NetworkManager[948]: <warn> Activation (wlan0/wireless): association took too long.
Oct  2 18:12:05 ubuntu NetworkManager[948]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Oct  2 18:12:05 ubuntu NetworkManager[948]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct  2 18:12:05 ubuntu NetworkManager[948]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Oct  2 18:12:20 ubuntu NetworkManager[948]: <warn> (wlan0): link timed out.

---

### Post by Doodaad on 2011-10-03
Well I ran all 406 updates and still no wireless. my laptop  is running  11.04 as well and connects fine.

Any help would be appreciated.

Kevin

---

### Post by azmyth on 2011-10-03
Do you have wireless-tools installed?

---

### Post by Bucky Ball on 2011-10-03
Add nothing to the WEP key. That will definitely not connect. The key has to be the correct length and, obviously, the correct combination of numbers and letters to match the router. 

If your laptop won't connect with the AP when it is sitting in the same place as the desktop but does connect outside why would you expect your desktop is going to connect without being moved closer to the router also?

---

### Post by Doodaad on 2011-10-04
Bucky,
I have a much better antenna (external) on my desktop I have 5 bars on it. I am sorry I forgot to add that my desktop will connect in windows 7.

Azmyth,
yes i do

sudo apt-get install wireless-tools
[sudo] password for shelly: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wireless-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am going to try installing gnome which is what my laptop is using and if that doesn't work ill try 11.10 beta... sigh

OK gnome didnt work and having other issues with kde not recognizing a new distro dvd or pendrive so I am closing this thread and trying the KDE forums since no one is interested...

---

