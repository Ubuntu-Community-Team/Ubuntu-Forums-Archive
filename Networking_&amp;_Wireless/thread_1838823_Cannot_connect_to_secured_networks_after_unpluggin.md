---
title: "Cannot connect to secured networks after unplugging wireless card"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by leejc on 2011-09-04
Hi,

I've been using my Belkin USB wireless network card on a desktop successfully. The other day, I unplugged it whilst it was in use and now when I plug it in, I can no longer see or connect to secured networks. I can still connect to unsecured networks.

Details:

**Machine Brand and Model**: Dell Vostro 410 (Desktop)
**Wireless Brand, Model and Wireless Chipset**: Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]

```
root@Lee-home:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:06:cd:c4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:be00(size=256) memory:fdaff000-fdafffff memory:fd9f0000-fd9fffff memory:fd900000-fd91ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: wlan0
       serial: 94:44:52:02:28:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-11-generic firmware=1.7 ip=10.42.43.38 link=no multicast=yes wireless=IEEE 802.11bg

``````

root@Lee-home:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

``````

root@Lee-home:~# lsb_release -d
Description:    Ubuntu 11.04

``````

root@Lee-home:~# uname -mr 
2.6.38-11-generic x86_64

``````

root@Lee-home:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


``````

root@Lee-home:~# lsmod 
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
arc4                   12529  2 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               682322  2 
soundcore              12680  1 snd
ttm                    76664  1 nouveau
drm_kms_helper         42136  1 nouveau
psmouse                73535  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   227534  4 nouveau,ttm,drm_kms_helper
rt73usb                27406  0 
i2c_algo_bit           13400  1 nouveau
crc_itu_t              12707  1 rt73usb
rt2x00usb              20330  1 rt73usb
video                  19438  1 nouveau
rt2x00lib              49235  2 rt73usb,rt2x00usb
mac80211              294370  2 rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
dcdbas                 14438  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
serio_raw              13166  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
floppy                 74120  0 
r8169                  48022  0 

```Syslog content after inserting the USB card (this is a superset of what appears in dmesg):

```

Sep  4 15:40:42 Lee-home kernel: [  260.320020] usb 2-3: new high speed USB device using ehci_hcd and address 4
Sep  4 15:40:43 Lee-home kernel: [  260.662784] cfg80211: Calling CRDA to update world regulatory domain
Sep  4 15:40:43 Lee-home kernel: [  260.667127] cfg80211: World regulatory domain updated:
Sep  4 15:40:43 Lee-home kernel: [  260.667130] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep  4 15:40:43 Lee-home kernel: [  260.667133] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.667136] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.667138] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.667140] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.667143] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951591] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951597] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951600] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951604] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951607] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951611] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951614] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951617] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951620] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951624] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951627] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951631] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951634] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951637] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951640] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951644] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951647] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951651] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951654] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951658] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951661] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951664] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951667] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951671] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951674] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951678] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.951681] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Sep  4 15:40:43 Lee-home kernel: [  260.951684] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
Sep  4 15:40:43 Lee-home kernel: [  260.958011] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Sep  4 15:40:43 Lee-home kernel: [  260.958907] Registered led device: rt73usb-phy0::radio
Sep  4 15:40:43 Lee-home kernel: [  260.958939] Registered led device: rt73usb-phy0::assoc
Sep  4 15:40:43 Lee-home kernel: [  260.958967] Registered led device: rt73usb-phy0::quality
Sep  4 15:40:43 Lee-home kernel: [  260.959439] usbcore: registered new interface driver rt73usb
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt73usb' ifindex: 3)
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): now managed
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): bringing up device.
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): preparing device.
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): deactivating device (reason: 2).
Sep  4 15:40:43 Lee-home kernel: [  261.069422] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  4 15:40:43 Lee-home NetworkManager[752]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/net/wlan0, iface: wlan0)
Sep  4 15:40:43 Lee-home NetworkManager[752]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): supplicant interface state:  starting -> ready
Sep  4 15:40:43 Lee-home NetworkManager[752]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Sep  4 15:40:43 Lee-home wpa_supplicant[837]: Failed to initiate AP scan.

``````
 root@Lee-home:~# iwlist wlan0 scan
wlan0            No scan results

```There are several secured wireless networks in range, and the one that machine previously connected to still works on my Ubuntu laptop / phone etc.

From the logs, I can see that it is the wpa_supplicant that is failing to scan for APs, so I created an unsecured network on my laptop called 'Noauth'. I could connect to this without any problems, i.e., I could ping my laptop from my desktop and vice-versa:

```

root@Lee-home:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: E6:CA:F8:FE:4E:E6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"Noauth"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000004e842b8
                    Extra: Last beacon: 1180ms ago
                    IE: Unknown: 00064E6F61757468
                    IE: Unknown: 010882040B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD070050F202000100

root@Lee-home:~# iwconfig wlan0 essid Noauth
          
root@Lee-home:~# iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Noauth"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: EE:57:B1:92:B5:D1   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

root@Lee-home:~# dhclient wlan0

root@Lee-home:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:06:cd:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 94:44:52:02:28:3a  
          inet addr:10.42.43.38  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::9644:52ff:fe02:283a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2944 (2.9 KB)  TX bytes:17482 (17.4 KB)

root@Lee-home:~# ping  10.42.43.1
PING 10.42.43.1 (10.42.43.1) 56(84) bytes of data.
64 bytes from 10.42.43.1: icmp_req=1 ttl=64 time=2.03 ms
64 bytes from 10.42.43.1: icmp_req=2 ttl=64 time=2.05 ms
64 bytes from 10.42.43.1: icmp_req=3 ttl=64 time=2.08 ms
^C
--- 10.42.43.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.036/2.059/2.088/0.042 ms

```Any ideas as to what can be wrong, or even tips on how to debug the wpa_supplicant hooked up to dbus / NetworkManager?

Many thanks in advance,

Lee

---

### Post by wildmanne39 on 2011-09-04
Hi, please post the results of this command:
```
lsusb
```
Thank you

---

### Post by leejc on 2011-09-04
Sorry, missed that out:

```

lee@Lee-home:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2573]
Bus 002 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by wildmanne39 on 2011-09-04
Hi, I do not see any thing wrong with the information you posted.

What is your encryption set on in your router?

It concerns me that the scan did not find any wireless networks. Please post the results of these commands.
```
dmesg | grep rt7
```
```
dmesg | grep wlan0
```
```
dmesg | egrep 'rt7|firm'
```
```
nm-tool
```
Thank you

---

### Post by praseodym on 2011-09-04
Do you really wanto to use an Ad-Hoc network, this means Internet Connection Sharing (ICS)?! If not, remove your profile in the Networkmanager-applet and create a new profile in "Infrastructure"-mode.

---

### Post by leejc on 2011-09-05
@wildmanne39: Encryption type is 'WPA/WPA2 Personal'. Here is the additional info:

```

lee@Lee-home:~$ dmesg | grep rt7
[   14.644328] Registered led device: rt73usb-phy0::radio
[   14.644351] Registered led device: rt73usb-phy0::assoc
[   14.644372] Registered led device: rt73usb-phy0::quality
[   14.644845] usbcore: registered new interface driver rt73usb

```

```

lee@Lee-home:~$ dmesg | grep wlan0
[   15.346446] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
```

lee@Lee-home:~$ dmesg | egrep 'rt7|firm'
[   14.644328] Registered led device: rt73usb-phy0::radio
[   14.644351] Registered led device: rt73usb-phy0::assoc
[   14.644372] Registered led device: rt73usb-phy0::quality
[   14.644845] usbcore: registered new interface driver rt73usb

```
```

lee@Lee-home:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:21:9B:06:CD:C4

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             disconnected
  Default:           no
  HW Address:        94:44:52:02:28:3A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```


@praseodym: That was because I created an unsecured an-hoc network to test the card without encryption. I have deleted all profiles in Network Manager.

Thank you to both of you for your help so far.

Lee

---

### Post by praseodym on 2011-09-05
Ad-Hoc NW means you are using a shared connection from another computer. You may want to use your own connection, arent you?

Unsecure NW are used with infrastructure mode and WEP or no encryption.

---

### Post by leejc on 2011-09-05
Hi praseodym, you are correct - I merely set-up the ad-hoc network to demonstrate that the card was at least partially functional, i.e., it could scan for and connect to unencrypted networks.

Cheers, Lee

---

### Post by wildmanne39 on 2011-09-05
Hi, change your encryption setting to just wpa2 not mixed mode and see if you can connect, you will have to disconnect your wired connection first.
Thank you

---

### Post by leejc on 2011-09-06
Hi, no joy - network is not even visible to a scan :-( Cheers

---

### Post by praseodym on 2011-09-06
I just saw, that your power management is "on", shutoff with:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
Control:

```
iwconfig
sudo iwlist scan
iwlist chan
rfkill list
route -n
cat /etc/resolv.conf
```

---

### Post by leejc on 2011-09-06
Hi, here's the command output:

```
lee@Lee-home:~$ sudo iwconfig wlan0 power off
``````
lee@Lee-home:~$ sudo service network-manager restart
network-manager start/running, process 1857

``````
lee@Lee-home:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````
lee@Lee-home:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```
```
lee@Lee-home:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

```
```
lee@Lee-home:~$ rfkill list
0: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```
lee@Lee-home:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```
```
lee@Lee-home:~$ cat /etc/resolv.conf
nameserver 10.42.43.1

```

Thanks again for your help,

Lee

---

### Post by praseodym on 2011-09-06
```
lee@Lee-home:~$ cat /etc/resolv.conf
nameserver [COLOR="Red"]10.42.43.1[/COLOR]
```
Is that a virtual machine?

---

### Post by leejc on 2011-09-06
> Is that a virtual machine?

No, bare metal.

Cheers,

Lee

---

### Post by nm_geo on 2011-09-06
Sorry misread on my part

---

### Post by wildmanne39 on 2011-09-06
Hi, here is a link that has directions for setting up your wireless so it can use encryption, scroll down the page to where it talks about the rt73 driver, I hope it helps.
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

---

### Post by leejc on 2011-09-08
Hi,

I get an error...
```

lee@Lee-Home:~$ sudo iwpriv wlan0 set AuthMode=WPAPSK
wlan0     no private ioctls.

```

Thanks,

Lee

---

