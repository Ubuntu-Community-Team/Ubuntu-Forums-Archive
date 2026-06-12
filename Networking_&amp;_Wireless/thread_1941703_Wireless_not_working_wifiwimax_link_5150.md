---
title: "Wireless not working wifi/wimax link 5150"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by ruslanbe on 2012-03-16
[FONT=Verdana][SIZE=2]Hello,
I can't find any wireless connections after installing ubuntu 11.10 [/SIZE][/FONT][SIZE=2]**[FONT=Verdana]3.0.0-16-generic i686 [/FONT]**[/SIZE][FONT=Verdana][SIZE=2](cable Internet is working)[/SIZE][/FONT][SIZE=2].
[/SIZE]          [FONT=Verdana][SIZE=2]machine type - lenovo sl400 thinkpad (laptop)
[/SIZE][/FONT][FONT=Verdana][SIZE=2]netwotk hardware - [/SIZE][/FONT][FONT=Verdana][SIZE=2]Intel Corporation WiMAX/WiFi Link 5150

**_ifconfig_**
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:96:b8:d2  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe96:b8d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21303162 (21.3 MB)  TX bytes:1505517 (1.5 MB)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)

[/SIZE][/FONT][SIZE=2]**_iwconfig_**
lo        no wireless extensions.

eth0      no wireless extensions.

wwan0     no wireless extensions.

wmx0      no wireless extensions.

 **_lsmod_**
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  8 
nvidia              10390874  43 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52460  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
i2400m_usb             35737  0 
i2400m                101240  1 i2400m_usb
wimax                  33525  1 i2400m
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cdc_ether              13312  0 
uvcvideo               67271  0 
usbnet                 25214  1 cdc_ether
cdc_wdm                17317  0 
cdc_acm                22305  0 
snd_seq_midi           13132  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
btusb                  18160  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                273980  0 
mac80211              393421  1 iwlagn
bluetooth             148839  23 bnep,rfcomm,btusb
r592                   17808  0 
memstick               15857  1 r592
psmouse                73673  0 
serio_raw              12990  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  2 iwlagn,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  0 
asus_laptop            19050  0 
sparse_keymap          13658  1 asus_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  3 
libahci                25727  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  43104  0 

**_sudo lshw -C network_**
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: WiMAX/WiFi Link 5150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fd6fe000-fd6fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:96:b8:d2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.0.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:e800(size=256) memory:f8fff000-f8ffffff memory:f8fe0000-f8feffff memory:f8f00000-f8f0ffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:2
       logical name: wmx0
       serial: 00:1d:e1:01:9f:61
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i2400m-fw-usb-1.5.sbcf link=no

_**sudo /etc/init.d/networking restart**_
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
[/SIZE]

---

### Post by ruslanbe on 2012-03-16
anyone?

---

### Post by chili555 on 2012-03-16
Hmmmm. Mighty suspicious:> machine type - lenovo sl400 thinkpad (laptop)However, among the modules running is:> [COLOR="Red"]asus[/COLOR]_laptop 19050 0
sparse_keymap 13658 1 asus_laptopLet's do some diagnostics. Please run and post:```
rfkill list all
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by ruslanbe on 2012-03-17
Thank you for your response and help! here is the diagnostics...
I want to start use ubuntu as my main operation system and the wireless problem is the one thing that stop me..

ruslan@ruslan-ThinkPad-SL:~$ **rfkill list all**
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

ruslan@ruslan-ThinkPad-SL:~$ **sudo modprobe iwlagn** -**_ nothing happend...:)_**
[sudo] password for ruslan: \

ruslan@ruslan-ThinkPad-SL:~**$ dmesg | grep iwl**
[   15.231345] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.231349] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   15.231427] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.231438] iwlagn 0000:03:00.0: setting latency timer to 64
[   15.231467] iwlagn 0000:03:00.0: Detected Intel(R) WiMAX/WiFi Link 5150 AGN, REV=0x44
[   15.253364] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x21b < 0x21e CALIB=0x4 < 0x4
[   15.275991] iwlagn 0000:03:00.0: PCI INT A disabled
[   15.276039] iwlagn: probe of 0000:03:00.0 failed with error -22

---

### Post by chili555 on 2012-03-17
> Unsupported (too old) EEPROM VER=0x21b < 0x21e CALIB=0x4 < 0x4Please see post #2 here: [http://ubuntuforums.org/showthread.php?t=1627219](http://ubuntuforums.org/showthread.php?t=1627219)> I have seen this issue reported a few times; I have not yet seen a solution.

---

