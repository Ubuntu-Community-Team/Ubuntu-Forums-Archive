---
title: "Wifi is not working even drivers are working properly"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by jyothidamu on 2011-07-02
HI there


 I have recently installed Ubuntu on my dell laptop everything is going on perfect i have tried to trouble shoot it could please check the below commands output and let me know please if i have to make any changes
 
]**indira@ubuntu:~$ lsb_release -a **
 No LSB modules are available. 
 Distributor ID:    Ubuntu 
 Description:    Ubuntu 11.04 
 Release:    11.04 
 Codename:    natty
 
**indira@ubuntu:~$ sudo lshw -c network **
[sudo] password for indira: 
  *-network                
       description: Wireless interface 
       product: Centrino Wireless-N 1000 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:26:c7:99:de:9a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:48 memory:f0400000-f0401fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 06 
       serial: f0:4d:a2:54:bb:6a 
       size: 100Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.81 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
       resources: irq:41 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff
  
**indira@ubuntu:~$ sudo rfkill list**
0: dell-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 

**indira@ubuntu:~$ lsmod **
Module                  Size  Used by 
cryptd                 20510  0  [/SIZE][/FONT]
aes_x86_64             17208  0  [/SIZE][/FONT]
aes_generic            38279  1 aes_x86_64 [/SIZE][/FONT]
joydev                 17606  0  [/SIZE][/FONT]
]binfmt_misc            17565  1  [/SIZE][/FONT]
parport_pc             36959  0  [/SIZE][/FONT]
ppdev                  17113  0  [/SIZE][/FONT]
snd_hda_codec_hdmi     28103  1  [/SIZE][/FONT]
snd_hda_codec_realtek   336693  1  [/SIZE][/FONT]
arc4                   12529  2  [/SIZE][/FONT]
snd_hda_intel          33211  2  [/SIZE][/FONT]
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel [/SIZE][/FONT]
snd_hwdep              13604  1 snd_hda_codec [/SIZE][/FONT]
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec [/SIZE][/FONT]
snd_seq_midi           13324  0  [/SIZE][/FONT]
snd_rawmidi            30486  1 snd_seq_midi [/SIZE][/FONT]
iwlagn                333500  0  [/SIZE][/FONT]
snd_seq_midi_event     14899  1 snd_seq_midi [/SIZE][/FONT]
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event [/SIZE][/FONT]
nouveau               682322  0  [/SIZE][/FONT]
snd_timer              29602  2 snd_pcm,snd_seq [/SIZE][/FONT]
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq [/SIZE][/FONT]
i915                  514985  8  [/SIZE][/FONT]
uvcvideo               72195  0  [/SIZE][/FONT]
videodev               82052  1 uvcvideo [/SIZE][/FONT]
iwlcore               167503  1 iwlagn [/SIZE][/FONT]
dell_wmi               12681  0  [/SIZE][/FONT]
mac80211              294370  2 iwlagn,iwlcore [/SIZE][/FONT]
psmouse                73535  0  [/SIZE][/FONT]
dell_laptop            13827  0  [/SIZE][/FONT]
sparse_keymap          13898  1 dell_wmi [/SIZE][/FONT]
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
ttm                    76664  1 nouveau [/SIZE][/FONT]
cfg80211              178528  3 iwlagn,iwlcore,mac80211 [/SIZE][/FONT]
dcdbas                 14438  1 dell_laptop [/SIZE][/FONT]
v4l2_compat_ioctl32    17078  1 videodev [/SIZE][/FONT]
drm_kms_helper         42136  2 nouveau,i915 [/SIZE][/FONT]
xhci_hcd               77643  0  [/SIZE][/FONT]
soundcore              12680  1 snd [/SIZE][/FONT]
serio_raw              13166  0  [/SIZE][/FONT]
intel_ips              18097  0  [/SIZE][/FONT]
drm                   227495  6 nouveau,ttm,i915,drm_kms_helper [/SIZE][/FONT]
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm [/SIZE][/FONT]
i2c_algo_bit           13400  2 nouveau,i915 [/SIZE][/FONT]
video                  19438  2 nouveau,i915 [/SIZE][/FONT]
lp                     17825  0  [/SIZE][/FONT]
parport                46458  3 parport_pc,ppdev,lp [/SIZE][/FONT]
ahci                   25951  1  [/SIZE][/FONT]
r8169                  48022  0  [/SIZE][/FONT]
libahci                26642  1 ahci [/SIZE][/FONT]

indira@ubuntu:~$ lsusb [/SIZE][/FONT]
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub [/SIZE][/FONT]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub [/SIZE][/FONT]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/SIZE][/FONT]
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc.  [/SIZE][/FONT]
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub [/SIZE][/FONT]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/SIZE][/FONT]

**indira@ubuntu:~$ lspci**[/SIZE][/FONT]
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18) [/SIZE][/FONT]
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) [/SIZE][/FONT]
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) [/SIZE][/FONT]
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) [/SIZE][/FONT]
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) [/SIZE][/FONT]
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) [/SIZE][/FONT]
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) [/SIZE][/FONT]
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) [/SIZE][/FONT]
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) [/SIZE][/FONT]
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) [/SIZE][/FONT]
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) [/SIZE][/FONT]
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) [/SIZE][/FONT]
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) [/SIZE][/FONT]
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) [/SIZE][/FONT]
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) [/SIZE][/FONT]
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) [/SIZE][/FONT]
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) [/SIZE][/FONT]
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1) [/SIZE][/FONT]
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 [/SIZE][/FONT]
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) [/SIZE][/FONT]
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) [/SIZE][/FONT]
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) [/SIZE][/FONT]
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) [/SIZE][/FONT]
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) [/SIZE][/FONT]
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05) [/SIZE][/FONT]
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05) [/SIZE][/FONT]
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) [/SIZE][/FONT]

indira@ubuntu:~$ 
[/SIZE][/FONT]


thank you
[/SIZE][/FONT]

---

### Post by chili555 on 2011-07-02
Network Manager is designed to *disallow* a wireless connection if you have wired connected. You do:> driver=r8169 driverversion=2.3LK-NAPI duplex=full [COLOR="Red"]ip=192.168.1.81[/COLOR]Disconnect the cable, wait a few moments and click the Network Manager icon. Do you see wireless networks? Can you click yours and connect?

---

### Post by nm_geo on 2011-07-02
This may sound crazy, but have you booted the laptop with the ethernet cable removed?  The network manager only likes one connection.

Opps the doctor is in the house... I be slow today doc

---

### Post by jyothidamu on 2011-07-03
> **chili555 said:**
> Network Manager is designed to *disallow* a wireless connection if you have wired connected. You do:Disconnect the cable, wait a few moments and click the Network Manager icon. Do you see wireless networks? Can you click yours and connect?
indira@ubuntu:~$ sudo lshw -c network 
[sudo] password for indira: 
  *-network                
       description: Wireless interface 
       product: Centrino Wireless-N 1000 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:26:c7:99:de:9a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:48 memory:f0400000-f0401fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 06 
       serial: f0:4d:a2:54:bb:6a 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:41 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff 
indira@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
           
indira@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:54:bb:6a   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:99:de:9a   
          inet6 addr: fe80::226:c7ff:fe99:de9a/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:13033 (13.0 KB)  TX bytes:12992 (12.9 KB) 

indira@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18) 
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1) 
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) 
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05) 
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
indira@ubuntu:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
indira@ubuntu:~$ lsmod 
Module                  Size  Used by 
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13604  1 snd_hda_codec 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi 
uvcvideo               72195  0 
iwlagn                333500  0 
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi 
nvidia              10709116  0 
snd_seq_midi_event     14899  1 snd_seq_midi 
i915                  514985  7 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
iwlcore               167503  1 iwlagn 
videodev               82052  1 uvcvideo 
v4l2_compat_ioctl32    17078  1 videodev 
snd_timer              29602  2 snd_pcm,snd_seq 
mac80211              294370  2 iwlagn,iwlcore 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              178528  3 iwlagn,iwlcore,mac80211 
drm_kms_helper         42136  1 i915 
drm                   227495  3 i915,drm_kms_helper 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop 
intel_ips              18097  0 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
psmouse                73535  0 
xhci_hcd               77643  0 
i2c_algo_bit           13400  1 i915 
serio_raw              13166  0 
video                  19438  1 i915 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp 
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci 
indira@ubuntu:~$ sudo rfkill list 
0: dell-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
indira@ubuntu:~$

---

### Post by jyothidamu on 2011-07-03
> **chili555 said:**
> Network Manager is designed to *disallow* a wireless connection if you have wired connected. You do:Disconnect the cable, wait a few moments and click the Network Manager icon. Do you see wireless networks? Can you click yours and connect?
indira@ubuntu:~$ sudo lshw -c network 
[sudo] password for indira: 
  *-network                
       description: Wireless interface 
       product: Centrino Wireless-N 1000 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:26:c7:99:de:9a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:48 memory:f0400000-f0401fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 06 
       serial: f0:4d:a2:54:bb:6a 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:41 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff 
indira@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
           
indira@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:54:bb:6a   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:99:de:9a   
          inet6 addr: fe80::226:c7ff:fe99:de9a/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:13033 (13.0 KB)  TX bytes:12992 (12.9 KB) 

indira@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18) 
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1) 
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) 
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05) 
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
indira@ubuntu:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
indira@ubuntu:~$ lsmod 
Module                  Size  Used by 
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13604  1 snd_hda_codec 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi 
uvcvideo               72195  0 
iwlagn                333500  0 
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi 
nvidia              10709116  0 
snd_seq_midi_event     14899  1 snd_seq_midi 
i915                  514985  7 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
iwlcore               167503  1 iwlagn 
videodev               82052  1 uvcvideo 
v4l2_compat_ioctl32    17078  1 videodev 
snd_timer              29602  2 snd_pcm,snd_seq 
mac80211              294370  2 iwlagn,iwlcore 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              178528  3 iwlagn,iwlcore,mac80211 
drm_kms_helper         42136  1 i915 
drm                   227495  3 i915,drm_kms_helper 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop 
intel_ips              18097  0 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
psmouse                73535  0 
xhci_hcd               77643  0 
i2c_algo_bit           13400  1 i915 
serio_raw              13166  0 
video                  19438  1 i915 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp 
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci 
indira@ubuntu:~$ sudo rfkill list 
0: dell-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
indira@ubuntu:~$   this is what i got when i booted the Ubuntu with out Ethernet cable

---

### Post by jyothidamu on 2011-07-03
> **nm_geo said:**
> This may sound crazy, but have you booted the laptop with the ethernet cable removed?  The network manager only likes one connection.

Opps the doctor is in the house... I be slow today doc
indira@ubuntu:~$ sudo lshw -c network 
[sudo] password for indira: 
  *-network                
       description: Wireless interface 
       product: Centrino Wireless-N 1000 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: wlan0 
       version: 00 
       serial: 00:26:c7:99:de:9a 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn 
       resources: irq:48 memory:f0400000-f0401fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 06 
       serial: f0:4d:a2:54:bb:6a 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:41 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff 
indira@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=14 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
           
indira@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:54:bb:6a   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:99:de:9a   
          inet6 addr: fe80::226:c7ff:fe99:de9a/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:13033 (13.0 KB)  TX bytes:12992 (12.9 KB) 

indira@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18) 
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06) 
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1) 
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000 
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) 
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05) 
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05) 
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05) 
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05) 
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
indira@ubuntu:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 0408:2fb1 Quanta Computer, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
indira@ubuntu:~$ lsmod 
Module                  Size  Used by 
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13604  1 snd_hda_codec 
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi 
uvcvideo               72195  0 
iwlagn                333500  0 
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi 
nvidia              10709116  0 
snd_seq_midi_event     14899  1 snd_seq_midi 
i915                  514985  7 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event 
iwlcore               167503  1 iwlagn 
videodev               82052  1 uvcvideo 
v4l2_compat_ioctl32    17078  1 videodev 
snd_timer              29602  2 snd_pcm,snd_seq 
mac80211              294370  2 iwlagn,iwlcore 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              178528  3 iwlagn,iwlcore,mac80211 
drm_kms_helper         42136  1 i915 
drm                   227495  3 i915,drm_kms_helper 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop 
intel_ips              18097  0 
soundcore              12680  1 snd 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm 
psmouse                73535  0 
xhci_hcd               77643  0 
i2c_algo_bit           13400  1 i915 
serio_raw              13166  0 
video                  19438  1 i915 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp 
ahci                   25951  1 
r8169                  48022  0 
libahci                26642  1 ahci 
indira@ubuntu:~$ sudo rfkill list 
0: dell-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
indira@ubuntu:~$  

this is the output of after booting the  Ubuntu with out Ethernet cable still its  not working

---

### Post by chili555 on 2011-07-03
You've given me a great deal of information but what I really need to know I asked above:> Disconnect the cable, wait a few moments and click the Network Manager icon. Do you see wireless networks? Can you click yours and connect? 

---

### Post by tachidok on 2011-08-07
Hi, 

I found a solution for this problem..

[B]1) The solution is here
     [http://ubuntuforums.org/showthread.php?t=1718211](http://ubuntuforums.org/showthread.php?t=1718211)

2) Next check this link
[http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/](http://berm0o0da.wordpress.com/2011/01/31/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa/))

And here his what did I do for fixing that solution

  - Do the part for installing kernel 2.6.28
[/B]sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-headers-2.6.38-1-generic linux-image-2.6.38-1-generic
 [B]  - The last line WILL THROW YOU AN ERROR (don't panic!!!!)
  - Download kernel 2.6.28.8 from [http://www.kernel.org/](http://www.kernel.org/)
[/B]
Unzip and install (here are the instructions, copied from the cited pages)[B]
ATTENTION: Changes the kernel name
  [/B]
**2.** Extract the package:
tar xvf linux-2.6.37.tar.bz2 (here change to kernel 2.6.38.8)[B]
3.[/B] use default *.config* file:
sudo cp  /boot/config-2.6.32-21-generic ~/linux-2.6.37 (here change again!!!!)
**4.** make and install:
cd ~/linux-2.6.37  (jeje, again)
make menuconfig   (install ncurses first and the ncurses-dev too)
make  (wait, be patient or take your dog for a walk!!!!) :popcorn:
make modules_install  
make install 
**5.** Create initrd:
sudo update-initramfs -k -c 2.6.38.8 (change the order to  sudo update-initramfs -c -k 2.6.38.8)

**6.** Update grub:
sudo update-grub

NOTE: Turn on the wireless!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

And now you have your wireless activated...
Enjoy it ... !!! :guitar::guitar::guitar::guitar:

---

