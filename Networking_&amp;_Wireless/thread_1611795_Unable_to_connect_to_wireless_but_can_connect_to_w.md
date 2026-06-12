---
title: "Unable to connect to wireless but can connect to wired"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Hannon565 on 2010-11-02
I am unable to connect to wireless network in ubuntu 10.10

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Network controller: Intel Corporation WiFi Link 5100
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
0a:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

```

lshw -c network
```
   *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:07:d3:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic-pae firmware=8.24.2.12 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:d1500000-d1501fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:ba:b3:53:4b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=147.252.229.179 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:d0120000-d0123fff ioport:9000(size=256) memory:d0100000-d011ffff

```

lsmod
```
Module                  Size  Used by
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
btusb                  11001  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
joydev                  8735  0 
snd_hda_codec_realtek   217980  1 
arc4                    1165  2 
snd_hda_intel          22203  2 
radeon                852383  3 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71571  2 snd_hda_intel,snd_hda_codec
iwlagn                179813  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
iwlcore               127479  1 iwlagn
ttm                    56825  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 radeon
mac80211              231541  2 iwlagn,iwlcore
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
drm                   168726  5 radeon,ttm,drm_kms_helper
videodev               43098  1 uvcvideo
cfg80211              144470  3 iwlagn,iwlcore,mac80211
v4l1_compat            13359  2 uvcvideo,videodev
intel_agp              26720  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 radeon
sony_laptop            29184  0 
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32075  3 ttm,drm,intel_agp
video                  18712  0 
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
firewire_ohci          21394  0 
sdhci_pci               6339  0 
sdhci                  15954  1 sdhci_pci
led_class               2633  1 sdhci
libahci                21731  3 ahci
firewire_core          46675  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
sky2                   45456  0 

```

i have noticed that the iwlagn driver isnt been used by anything

all help be much appericated and will post any other commands wanted

---

### Post by chili555 on 2010-11-02
Network Manager is designed to not allow a wireless connection if you have a wired connection, which you do.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

Is the wireless switch switched on?```
rfkill list all
```> i have noticed that the iwlagn driver isnt been used by anything
Not exactly true:> iwlagn                179813  0 
iwlcore               127479  1 iwlagn
mac80211              231541  2 iwlagn,iwlcore
cfg80211              144470  3 iwlagn,iwlcore,mac80211
It looks busy to me!

---

### Post by Hannon565 on 2010-11-02
I don't usually have wired connection avaliable just tried to it to see if works and did.
rfkill list all
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I can see the wireless connection but can't connect to it with or without the wep key on it.
When connect it trys then fails. It works on every other device in the house.

---

### Post by chili555 on 2010-11-02
Let's see if there are any interesting messages about this:```
dmesg | grep -e iwlagn -e wlan
```Thanks.

---

### Post by Hannon565 on 2010-11-02
```


[   18.655691] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   18.655694] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   18.655779] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.655808] iwlagn 0000:06:00.0: setting latency timer to 64
[   18.656556] iwlagn 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   18.710199] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   18.710365] iwlagn 0000:06:00.0: irq 49 for MSI/MSI-X
[   18.758221] iwlagn 0000:06:00.0: loaded firmware version 8.24.2.12
[   20.229138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.709080] wlan0: authenticate with 00:17:3f:3a:bf:ce (try 1)
[   47.713915] wlan0: authenticated
[   47.713954] wlan0: associate with 00:17:3f:3a:bf:ce (try 1)
[   47.716252] wlan0: RX AssocResp from 00:17:3f:3a:bf:ce (capab=0x411 status=0 aid=3)
[   47.716255] wlan0: associated
[   47.718058] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   58.280072] wlan0: no IPv6 routers present
[   96.260078] wlan0: deauthenticating from 00:17:3f:3a:bf:ce by local choice (reason=3)
[  217.550163] wlan0: authenticate with 00:17:3f:3a:bf:ce (try 1)
[  217.554965] wlan0: authenticated
[  217.555017] wlan0: associate with 00:17:3f:3a:bf:ce (try 1)
[  217.557345] wlan0: RX AssocResp from 00:17:3f:3a:bf:ce (capab=0x411 status=0 aid=3)
[  217.557354] wlan0: associated
```

Thanks for all your help

---

### Post by chili555 on 2010-11-02
> [  217.550163] wlan0: authenticate with 00:17:3f:3a:bf:ce (try 1)
[  217.554965] wlan0: authenticated
[  217.555017] wlan0: associate with 00:17:3f:3a:bf:ce (try 1)
[  217.557345] wlan0: RX AssocResp from 00:17:3f:3a:bf:ce (capab=0x411 status=0 aid=3)
[  217.557354] [COLOR="Red"]wlan0: associated[/COLOR]It looks connected to me. Please run:```
ifconfig wlan0
```Do you have an IP address like this?> $ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 99:19:d2:c2:1b:88
          [COLOR="Red"]inet addr:192.168.1.108[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
[...]Can you ping the gateway/router?```
ping -c3 192.168.1.1
```Substitute your router's address if it's not 192.168.1.1.

---

### Post by Hannon565 on 2010-11-02
```

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:07:d3:1c  
          inet6 addr: fe80::222:fbff:fe07:d31c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6833 (6.8 KB)


```

and for ping -c3 command, I got Network is unreachable.

---

### Post by Hannon565 on 2010-11-04
Has no one had problem like this before?

---

### Post by irv on 2010-11-04
> **Hannon565 said:**
> Has no one had problem like this before?

You never said what laptop you have and what wifi card you are using.
First if you are on a wire, goto system> Administration> Additional Drivers. It should do a search and find if you need a wifi driver installed. If it finds the one you need, just select it and close the dialog box. Just unplug the network cable and it should find you wireless network.
I had the same problem with my Dell Inspiron 1521, and that is all I had to do.

---

### Post by chili555 on 2010-11-04
With all respect to our colleague irv, the driver is in place and working:```
[   18.655691] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   18.655694] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   18.655779] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.655808] iwlagn 0000:06:00.0: setting latency timer to 64
[   18.656556] [COLOR="Red"]iwlagn[/COLOR] 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   18.710199] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   18.710365] iwlagn 0000:06:00.0: irq 49 for MSI/MSI-X
[   18.758221] iwlagn 0000:06:00.0: loaded firmware version 8.24.2.12
[   20.229138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.709080] wlan0: authenticate with 00:17:3f:3a:bf:ce (try 1)
[   47.713915] wlan0: authenticated

```

---

### Post by irv on 2010-11-04
> **chili555 said:**
> With all respect to our colleague irv, the driver is in place and working:```
[   18.655691] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   18.655694] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   18.655779] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.655808] iwlagn 0000:06:00.0: setting latency timer to 64
[   18.656556] [COLOR="Red"]iwlagn[/COLOR] 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   18.710199] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   18.710365] iwlagn 0000:06:00.0: irq 49 for MSI/MSI-X
[   18.758221] iwlagn 0000:06:00.0: loaded firmware version 8.24.2.12
[   20.229138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.709080] wlan0: authenticate with 00:17:3f:3a:bf:ce (try 1)
[   47.713915] wlan0: authenticated

```

Very good. I alway like starting from the beginning. I have seen others out here that have the same problem as you. I still think it would be nice to know what hardware you are using? That way if others with the same hardware could just in on getting you some help with this problem.

---

### Post by Hannon565 on 2010-11-04
The exact system i m using is a sony vaio vgn-fw31m
The wireless card: Intel(R) WiFi Link 5100 AGN
Forgot to mention its dual booted system with Windows 7 and Ubuntu 10.10
If any other info about my system you need i have no problem suppling it

---

### Post by irv on 2010-11-04
Here is a list of thread with similar issues. Maybe you can find some help in one of these posts.
[http://ubuntuforums.org/search.php?searchid=77158892]("http://ubuntuforums.org/search.php?searchid=77158892")

---

