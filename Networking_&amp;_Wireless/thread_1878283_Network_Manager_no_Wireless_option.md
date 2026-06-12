---
title: "Network Manager no Wireless option"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by Esix on 2011-11-09
I understand if you think, 'not this again?!' But I've been trying to solve this myself over two months now, with every possible tool and tutorial, but I can't get it solved. So I can't be blamed for not searching and trying. 

I just installed a clean Xubuntu, so I wont be bothered by other wireless tools or other installed software. I've installed Ubuntu and Xubuntu many times before to clean everything to get Wireless working well, but always failed. 

I know of WICD. But WICD only works well at home. I mainly use this laptop on my university and WICD won't connect to the university network. The main solution would be getting wireless to work on the default network manager.   

To be as clear as possible here is a Thumbnail: 
[[IMG]http://img18.imageshack.us/img18/1750/nowireless.png[/IMG]]("http://imageshack.us/photo/my-images/18/nowireless.png/")

You clearly see, 'Wireless Networks' is just grey and not white to click on. I can't 'Enable Wireless'. If I click on it nothing happens. 

**1 ) Machine Brand and Model (PC/Laptop)**
Lenovo IdeaPad V560

[B]Wireless Brand, Model and Wireless Chipset (Sorry grep won't put out any information):
[/B][FONT=monospace]lspci:
```

esixx@EsixX:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```[/FONT]lsusb:
```

esixx@EsixX:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 004: ID 1c7a:0801 LighTuning Technology Inc. 
Bus 001 Device 005: ID 04f2:b18a Chicony Electronics Co., Ltd 

```[B]3 ) check interface:
[/B]ifconfig
```

esixx@EsixX:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:30:eb:88  
          inet6 addr: fe80::f2de:f1ff:fe30:eb88/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7240 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:13181261 (13.1 MB)  TX bytes:1003412 (1.0 MB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```iwconfig:
```

esixx@EsixX:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```[B]4 ) Check for modules (sorry grep won't put out any information):
[/B]lsmod:```
esixx@EsixX:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  12 
bnep                   18436  2 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
wl                   2568210  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
lib80211               14991  1 wl
bcma                   20219  0 
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
brcmsmac              631693  0 
joydev                 17693  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmutil               17837  1 brcmsmac
mac80211              310872  1 brcmsmac
btusb                  18600  2 
bluetooth             166112  23 rfcomm,bnep,btusb
cfg80211              199587  2 brcmsmac,mac80211
snd                    68266  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
i915                  566711  7 
acer_wmi               23948  0 
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
crc_ccitt              12667  1 brcmsmac
soundcore              12680  1 snd
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
ideapad_laptop         13871  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
serio_raw              13166  0 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
mei                    41480  0 
lp                     17799  0 
wmi                    19256  1 acer_wmi
intel_ips              18089  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci
```**5 ) Kernel boot messages**
dmesg | grep "wlan":
```

esixx@EsixX:~$ dmesg | grep "wlan"
[   56.811033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.362402] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.084346] ADDRCONF(NETDEV_UP): wlan0: link is not ready
esixx@EsixX:~$ dmesg | grep "wlan_module_name"
esixx@EsixX:~$ dmesg | grep "lan"
[    7.564546] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.564547] [drm] Driver supports precise vblank timestamp query.
[    7.969964] elantech: assuming hardware version 2, firmware version 4.0.2
[    8.037803] elantech: Synaptics capabilities query result 0x68, 0x18, 0x0c.
[    8.217497] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input7
[   56.811033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.362402] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   63.084346] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```[B]6 ) Network configuration
[/B]sudo lshw -C network:
```

esixx@EsixX:~$ sudo lshw -C network
[sudo] password for esixx: 
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:30:eb:88
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=10.0.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f2400000-f243ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: ac:81:12:25:f5:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f2500000-f2503fff
```[B]7 ) Scan for networks:
[/B]iwlist scan:
```

esixx@EsixX:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

```[B]8 ) Ubuntu Version: 
[/B]```

esixx@EsixX:~$ lsb_release -d
Description:    Ubuntu 11.10

[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B][code]
esixx@EsixX:~$ uname -mr
3.0.0-12-generic x86_64

```**10 ) Restarting the network:**
```

esixx@EsixX:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

```

---

### Post by Esix on 2011-11-09
bump

---

### Post by praseodym on 2011-11-09
Hi,

blacklist the modules **bcma**, **brcmsmac**, and **brcm80211**, and reboot.

---

