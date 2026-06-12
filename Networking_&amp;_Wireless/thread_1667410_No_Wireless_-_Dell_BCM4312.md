---
title: "No Wireless - Dell BCM4312"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by cesc04 on 2011-01-14
Hi guys,

New here and new to Ubuntu/Linux. Loving it all apart from wireless...gone through countless threads here, there and everywhere over the last couple of days trying to get it to work.

I have a Dell Studio XPS1645 running Ubuntu 10.10, with what seems to be the problematic Broadcom BCM4312 card. I'm using the b43 kernel driver. Here's a bunch of info...

```

michael@michael-Studio-XPS-1645:~$ lspci -nn | grep 'Broadcom'
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)

```

Tethering off my phone now - hence the top entry..


```

michael@michael-Studio-XPS-1645:~$ ifconfig
easytether0 Link encap:Ethernet  HWaddr 02:00:54:74:68:72  
          inet addr:192.168.117.2  Bcast:192.168.117.255  Mask:255.255.255.0
          inet6 addr: fe80::54ff:fe74:6872/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:10772562 (10.7 MB)  TX bytes:489742 (489.7 KB)

eth0      Link encap:Ethernet  HWaddr b8:ac:6f:66:2c:5e  
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
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:1f:87:fe  
          inet6 addr: fe80::7ae4:ff:fe1f:87fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5936 (5.9 KB)

```


```
michael@michael-Studio-XPS-1645:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

easytether0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
michael@michael-Studio-XPS-1645:~$ lsmod
Module                  Size  Used by
arc4                    1497  2 
b43                   187931  0 
mac80211              266657  1 b43
cfg80211              170293  2 b43,mac80211
nls_utf8                1453  1 
isofs                  34218  1 
cryptd                  8140  0 
aes_x86_64              7936  249 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
snd_hda_codec_atihdmi     3079  1 
rfcomm                 40755  4 
sco                     9954  2 
binfmt_misc             7984  1 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
joydev                 11363  0 
snd_hda_codec_idt      64667  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_midi            5932  0 
snd_hwdep               6660  1 snd_hda_codec
fglrx                2523725  124 
snd_rawmidi            22207  1 snd_seq_midi
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi_event      7291  1 snd_seq_midi
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                62080  0 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
serio_raw               4910  0 
soundcore               1240  1 snd
i7core_edac            18090  0 
edac_core              46822  1 i7core_edac
btusb                  12929  2 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
bluetooth              59213  9 rfcomm,sco,bnep,l2cap,btusb
dell_wmi                3372  0 
lp                     10201  0 
dcdbas                  6910  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
usb_storage            50372  1 
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
tg3                   135768  0 
ahci                   21857  0 
libahci                26167  4 ahci
ssb                    46169  1 b43
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  2 b43,sdhci
crc_itu_t               1739  1 firewire_core
video                  22176  0 
output                  2527  1 video

```

```
michael@michael-Studio-XPS-1645:~$ dmesg | grep "wlan"
[  563.048141] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  579.170095] wlan0: Trigger new scan to find an IBSS to join
[  590.022449] wlan0: no IPv6 routers present
[  602.873219] wlan0: Selected IBSS BSSID 86:ff:c1:51:13:25 based on configured SSID
[ 2210.328194] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2228.896541] wlan0: Trigger new scan to find an IBSS to join
[ 2230.329038] wlan0: Selected IBSS BSSID 86:ff:c1:51:13:25 based on configured SSID
[ 2239.620947] wlan0: no IPv6 routers present
```

```
michael@michael-Studio-XPS-1645:~$ sudo lshw -C network
[sudo] password for michael: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0900000-f0903fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 10
       serial: b8:ac:6f:66:2c:5e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:53 memory:f0d00000-f0d0ffff
  *-network:0
       description: Ethernet interface
       physical id: 4
       logical name: easytether0
       serial: 02:00:54:74:68:72
       size: 10MB/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=192.168.117.2 link=yes multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       physical id: 5
       logical name: wlan0
       serial: 78:e4:00:1f:87:fe
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
```

```
michael@michael-Studio-XPS-1645:~$ uname -mr
2.6.35-22-generic x86_64

```

As a bit of background, ive read there is a problem with my card and my release, but the solution here ([http://ubuntuforums.org/showthread.php?t=1604868&highlight=bcm4312](http://ubuntuforums.org/showthread.php?t=1604868&highlight=bcm4312)) has not worked. 

I've tried switching between the b43 and sta driver - and looks as though im closer with the b43 (can someone confirm this is the right driver of the two). I can see networks (cant see any with the sta driver - wireless is not even enabaled with sta), but cannot connect to any....be they open, WEP or WPA.

I've tried WICD, and have got various errors such as bad password and cannot obtain IP address.

Truly at a loss and would be extremely grateful for any help or guidance.

Thanks in advance.

---

### Post by bkratz on 2011-01-14
For some reason it double posted!

---

### Post by bkratz on 2011-01-14
Well the first thing I notice is 

wlan0     IEEE 802.11bg  ESSID:off/any  
          [COLOR="Red"]Mode:Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


Ad-hoc is between computers, you really want managed to connect with an A/P

You might try

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```

and repeat your tests

---

### Post by cesc04 on 2011-01-15
thanks for your reply bkratz.

Unfortunately it didnt work. still cannot connect.

By the way, in my haste to get as much info in as possible, i probably forgot the most important piece. 

I'm trying to connect to an ad-hoc network setup on Windows 7, with a usb wireless adaptor. Unfortunately i dont have a wireless router so im using the adaptor. This works no problem if i try to connect with an another windows 7 client.

Dmesg shows some of the following info after making ur changes and trying to connect....

b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.

wlan0: no IPv6 routers present
ADDRCONF(NETDEV_UP) wlan0: link is not ready

Please let me know if you need more info.

Thanks again.

---

