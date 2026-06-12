---
title: "Wireless Atheros not working on hp g6-2209se running ubuntu 12.04"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by modsaid on 2013-01-20
Hi all,

I am a bit new here, but not totally new to ubuntu... 

I recently bought a new hp pavilion G6-2209se [http://bit.ly/13TBP8j](http://bit.ly/13TBP8j) that is originally bought running windows8

I have removed the 5400 rpm hard driver, and used my old laptops's sshd hard drive which had dual boat ubuntu 12.04 and windows 7 installed. I had to configure BIOS for legacy boot options to make it work normally on MBR based hard drives. Anyway, to cut it short.


Wireless is currently working well on Windows 7 installation..  but not on ubuntu 12.04

1) Machine Brand and Model (PC/Laptop):

hp pavilion G6-2209se  [http://bit.ly/13TBP8j](http://bit.ly/13TBP8j)

2) Wireless Brand, Model and Wireless Chipset:


> 
$ lspci

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]
07:00.0 Network controller: Atheros Communications Inc. Device 0036 (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)

> $ lspci -v
...
07:00.0 Network controller: Atheros Communications Inc. Device 0036 (rev 01)
	Subsystem: Hewlett-Packard Company Device 18e3
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at c3500000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at 9fb00000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
....




> ~  $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 04e8:6881 Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 004: ID 0cf3:311f Atheros Communications, Inc. 
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 


> ~  $  lspci -nn | grep 'Ather'
07:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)


3 ) check interface:

>  $ ifconfig
eth1      Link encap:Ethernet  HWaddr 84:34:97:75:73:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:543498 (543.4 KB)  TX bytes:543498 (543.4 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.50  P-t-P:10.8.0.49  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:157996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:169807399 (169.8 MB)  TX bytes:45150595 (45.1 MB)

usb0      Link encap:Ethernet  HWaddr 8a:b9:59:72:c3:b6  
          inet addr:192.168.42.103  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::88b9:59ff:fe72:c3b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169230 errors:3 dropped:0 overruns:0 frame:3
          TX packets:145653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:188597933 (188.5 MB)  TX bytes:64775841 (64.7 MB)


> $  iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth1      no wireless extensions.

tun0      no wireless extensions.




4 ) Check for modules:

>  $ lsmod
Module                  Size  Used by
nls_utf8               12557  2 
isofs                  40257  2 
rndis_host             13855  0 
cdc_ether              13494  1 rndis_host
usbnet                 26168  2 rndis_host,cdc_ether
pci_stub               12622  1 
vboxpci                23237  0 
vboxnetadp             13382  0 
vboxnetflt             23478  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  1 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
compat                 13575  3 rndis_host,cdc_ether,usbnet
snd_hda_intel          33773  3 
fglrx                3264017  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
hp_accel               25976  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lis3lv02d              19876  1 hp_accel
soundcore              15091  1 snd
input_polldev          13896  1 lis3lv02d
psmouse                97485  0 
cdc_acm                26821  0 
serio_raw              13211  0 
i915                  477602  2 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         46978  1 i915
mei                    41616  0 
drm                   241971  3 i915,drm_kms_helper
wmi                    19256  1 hp_wmi
mac_hid                13253  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
uas                    18180  0 
usb_storage            49198  0 
r8169                  62154  0 



6 ) Network configuration


>  $  lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c3500000-c357ffff memory:9fb00000-9fb0ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 05
       serial: 84:34:97:75:73:df
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:c3404000-c3404fff memory:c3400000-c3403fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 8a:b9:59:72:c3:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.103 link=yes multicast=yes

of course none of the devices support scanning

8 ) Ubuntu Version: 

>  $ lsb_release -d
Description:	Ubuntu 12.04.1 LTS

9) Kernel/Architecture

> $ uname -mr
3.2.0-36-generic x86_64


10) restarting

>  $ /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                 


The wireless lid is always orange (indicating disabled).. but i do not have any physical button to switch it on or off... i've also tried rfkill to make sure it is not disabled

>  $ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


When I searched for windows drivers, i only found the Win8 based drivers on hp support website [http://bit.ly/Xqz48f](http://bit.ly/Xqz48f)

not even windows 7... which sucks..


Any help is appreciate it

---

### Post by gordintoronto on 2013-01-20
See this thread:
[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)

---

### Post by modsaid on 2013-01-21
> **gordintoronto said:**
> See this thread:
[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)


That didn't work for me, although it seems the same wireless hardware according to  "lspci -nn | grep Atheros" 



> 07:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)

---

### Post by modsaid on 2013-01-21
and when i try now when running "sudo modprobe ath9k"  is that warning

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.

---

### Post by modsaid on 2013-01-21
Finally worked after removing the windows driver installed via windows-wireless-driver too

thanks @gordintoronto,  the other thread really worked fine :)

---

