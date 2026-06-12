---
title: "Ubuntu 12.04 doesn't recognize my wireless card"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Varg_Gorgon on 2012-12-17
I upgraded to the latest version of Ubuntu through update manager. When I turn-on the computer, a screen shows up saying  "waiting for wireless connection" but it never finds it. Moreover, the  wifi button does not light at all, but if I do a wired connection, then that button starts to light  again. 

I tried to install the broadcom driver as explained here: [http://askubuntu.com/questions/13031...-does-not-work]("http://askubuntu.com/questions/130312/upgraded-to-ubuntu-12-04-now-wireless-does-not-work")  and it didn't work. In fact, when I tried the first command, the  terminal said it couldn't remove anything because it wasn't installed. 

I'm using the 64 bit version and I have an Intel Corporation WiFi Link 5100 wireless card.

---

### Post by ahallubuntu on 2012-12-17
The Broadcom driver is for a Broadcom wireless card.  It would have no effect on an Intel wireless card.  The 5100 is supported in all recent versions of Ubuntu (I have the same card in my laptop), so you should not have to install any driver for it.

Here is the post outlining what information to provide to get help with wireless issues:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Varg_Gorgon on 2012-12-18
Ok ahallubuntu. Here's the info:

**1 ) Machine Brand and Model (PC/Laptop)**: Dell Studio 17

[B]2 ) Wireless Brand, Model and Wireless Chipset:
lspci: 
[/B][PHP]04:00.0 Network controller: Intel Corporation WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)[/PHP][B]

lsusb: 
[/B][PHP]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:63fa Microdia 
Bus 007 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse[/PHP][B][B]3 ) check interface:
ifconfig: 
[/B][/B][PHP]eth0      Link encap:Ethernet  HWaddr 00:22:19:f0:b0:30  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fef0:b030/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:824401 (824.4 KB)  TX bytes:44799 (44.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:90:61:0c  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:fe90:610c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17388432 (17.3 MB)  TX bytes:1307662 (1.3 MB)[/PHP]**iwconfig:**
[PHP]lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"dlink1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:AF:F7:DA:F2:B7   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:102   Missed beacon:0

eth0      no wireless extensions.[/PHP]
[B]4 ) Check for modules:
[/B][PHP]Module                  Size  Used by
usbhid                 47199  0 
hid                    99592  1 usbhid
snd_hrtimer            12744  1 
vesafb                 13844  1 
joydev                 17693  0 
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
dell_laptop            18119  0 
r592                   18144  0 
dcdbas                 14490  1 dell_laptop
fglrx                3263886  158 
iwlwifi               397012  0 
r852                   18277  0 
sm_common              16865  1 r852
nand                   54955  2 r852,sm_common
nand_ids               12723  1 nand
mtd                    33087  2 sm_common,nand
nand_bch               13147  1 nand
bch                    22061  1 nand_bch
mac80211              506816  1 iwlwifi
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72627  0 
nand_ecc               13230  1 nand
memstick               16569  1 r592
psmouse                97443  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
serio_raw              13211  0 
cfg80211              205544  2 iwlwifi,mac80211
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
soundcore              15091  1 snd
ir_jvc_decoder         12507  0 
wmi                    19256  1 dell_wmi
ir_rc6_decoder         12507  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rc_rc6_mce             12502  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
ite_cir                25775  0 
video                  19596  0 
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,ite_cir
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
sdhci_pci              18826  0 
firewire_core          63558  1 firewire_ohci
sdhci                  33205  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
tg3                   152032  0 [/PHP][B][B]5 ) Kernel boot messages
[/B][/B][PHP][   21.142910] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.142912] Copyright(c) 2003-2011 Intel Corporation
[   21.142970] iwlwifi 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.143024] iwlwifi 0000:04:00.0: setting latency timer to 64
[   21.143040] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[   21.143042] iwlwifi 0000:04:00.0: pci_resource_base = ffffc90000674000
[   21.143044] iwlwifi 0000:04:00.0: HW Revision ID = 0x0
[   21.153489] iwlwifi 0000:04:00.0: irq 47 for MSI/MSI-X
[   21.153643] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   21.153870] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   21.184577] iwlwifi 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   21.184580] iwlwifi 0000:04:00.0: Device SKU: 0Xf0
[   21.188490] r592: driver successfully loaded
[   21.188900] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.214118] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.259891] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.291527] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   21.312549] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.312613] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   21.312642] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   21.318445] cfg80211: World regulatory domain updated:
[   21.318448] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.318451] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.318453] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.318456] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.318458] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.318461] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.369280] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   21.369455] Registered led device: phy0-led
[   21.369487] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   21.377232] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.389771] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   21.390057] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.390150] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   21.390180] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   21.410320] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   21.410387] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   21.742044] Bluetooth: Core ver 2.16
[   21.742086] NET: Registered protocol family 31
[   21.742088] Bluetooth: HCI device and connection manager initialized
[   21.742090] Bluetooth: HCI socket layer initialized
[   21.742092] Bluetooth: L2CAP socket layer initialized
[   21.742436] Bluetooth: SCO socket layer initialized
[   21.747373] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.747376] Bluetooth: BNEP filters: protocol multicast
[   21.762011] Bluetooth: RFCOMM TTY layer initialized
[   21.762016] Bluetooth: RFCOMM socket layer initialized
[   21.762018] Bluetooth: RFCOMM ver 1.11
[   21.772847] ppdev: user-space parallel port driver
[   21.788333] type=1400 audit(1355880051.434:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=820 comm="apparmor_parser"
[   21.788779] type=1400 audit(1355880051.434:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=820 comm="apparmor_parser"
[   21.934656] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input12
[   21.955222] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input13
[   22.006332] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[   22.006335] vesafb: scrolling: redraw
[   22.006337] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   22.010189] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011800000, using 3904k, total 3904k
[   22.010336] Console: switching to colour frame buffer device 144x54
[   22.010358] fb0: VESA VGA frame buffer device
[   22.794855] tg3 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex
[   22.794858] tg3 0000:08:00.0: eth0: Flow control is on for TX and on for RX
[   22.795291] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.298283] init: failsafe main process (764) killed by TERM signal
[   24.347230] type=1400 audit(1355880053.990:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1010 comm="apparmor_parser"
[   24.347238] type=1400 audit(1355880053.990:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1011 comm="apparmor_parser"
[   24.357172] type=1400 audit(1355880054.002:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1012 comm="apparmor_parser"
[   24.357539] type=1400 audit(1355880054.002:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1012 comm="apparmor_parser"
[   24.357751] type=1400 audit(1355880054.002:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1012 comm="apparmor_parser"
[   24.369301] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   24.372349] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   24.489578] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   24.492643] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   24.497914] init: gdm main process (1101) killed by TERM signal
[   24.539450] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.539692] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.050262] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   25.050924] [fglrx] Firegl kernel thread PID: 1312
[   25.050994] [fglrx] Firegl kernel thread PID: 1313
[   25.051061] [fglrx] Firegl kernel thread PID: 1314
[   25.051185] [fglrx] IRQ 50 Enabled
[   25.517200] [fglrx] Gart USWC size:1236 M.
[   25.517203] [fglrx] Gart cacheable size:489 M.
[   25.517208] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   25.517210] [fglrx] Reserved FB block: Unshared offset:fc21000, size:3df000 
[   25.517213] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   32.092070] wlan0: authenticate with 1c:af:f7:da:f2:b7 (try 1)
[   32.094422] wlan0: authenticated
[   32.099140] wlan0: associate with 1c:af:f7:da:f2:b7 (try 1)
[   32.102763] wlan0: RX AssocResp from 1c:af:f7:da:f2:b7 (capab=0x431 status=0 aid=2)
[   32.102768] wlan0: associated
[   32.107707] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.636102] usb 7-2: new low-speed USB device number 2 using uhci_hcd
[   73.832413] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input14
[   73.832675] generic-usb 0003:046D:C03D.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
[   73.832690] usbcore: registered new interface driver usbhid
[   73.832692] usbhid: USB HID core driver
[  542.264061] CE: hpet increased min_delta_ns to 20113 nsec
[/PHP][B][B][B]6 ) Network configuration:

[/B][/B][/B]  [PHP]*-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:90:61:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-34-generic firmware=8.83.5.1 build 33692 ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:f0:b0:30
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v2.17 ip=192.168.0.105 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:fc100000-fc10ffff
[/PHP][B]7 ) Scan for networks:
[/B][PHP]lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:AF:F7:DA:F2:B7
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"dlink1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005499c51d80
                    Extra: Last beacon: 64524ms ago
                    IE: Unknown: 0006646C696E6B31
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000000000000100000001CAFF7DAF2B710210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363135100800020086103C000103104900140024E26002000101600000020001600100020001
                    IE: Unknown: DD050050F20500

eth0      Interface doesn't support scanning.
[/PHP][B][B]8 ) Ubuntu Version: 

[/B][/B][PHP]Description:    Ubuntu 12.04.1 LTS[/PHP][B]9 ) Kernel/architecture (including 32 vs. 64 bit): 

[/B][PHP]3.2.0-34-generic x86_64[/PHP][B]10 ) Restarting the network:
[/B]
[PHP]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces... [/PHP][B]

11) I removed the Broadcom driver I installed as it doesn't affect my Intel wireless card. I used: sudo apt-get remove bcmwl-kernel-source

[/B][PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 21 not upgraded.
After this operation, 3,514 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 415717 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic[/PHP]

---

### Post by haqking on 2012-12-18
Can you browse the Internet ? cause according to that you are connected to a Wireless Network called "dlink1"

Your wireless is working fine and the device is Wlan0

---

### Post by Varg_Gorgon on 2012-12-18
that's because I did all the commands while having a wired connection.

---

### Post by haqking on 2012-12-18
> **Varg_Gorgon said:**
> that's because I did all the commands while having a wired connection.

Your ouptut shows you as being connected to a wireless network "dlink1" and your wireless is working.

Can you browse the Internet when not wired ?

---

### Post by Varg_Gorgon on 2012-12-18
Here's iwconfig without the wired connection: 

[PHP]lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.[/PHP]

Also, without the wired connection I can't browse the Internet. I think it shows like that because I configured my wireless network connection (it has a name and the WEP key).  Just for clarification, the name of the wireless connection and that of the router is the same so I guess that's why it shows up like that. Also, technically speaking, as per the "network connections" tool, I haven't configured a wired connection just a wireless one.

---

### Post by Varg_Gorgon on 2012-12-19
I resolved my issue by following the instructions here: [http://handytutorial.com/setting-up-wireless-network-in-ubuntu-12-04-precise/](http://handytutorial.com/setting-up-wireless-network-in-ubuntu-12-04-precise/)

I removed network manager and replaced it with wicd. Simple enough.

---

