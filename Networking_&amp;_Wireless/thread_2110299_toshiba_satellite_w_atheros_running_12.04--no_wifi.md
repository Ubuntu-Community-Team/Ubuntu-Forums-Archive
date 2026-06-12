---
title: "toshiba satellite w/ atheros running 12.04--no wifi"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by happyturtle on 2013-01-29
I just installed ubuntu 12.04, and although I can get online with an ethernet cord, I have no wifi access. 
I've run most of the code provided in [this post]("http://ubuntuforums.org/showthread.php?p=6183681"). I'd be happy to give details, but this is what seems most important to me: 
$lspci gives me a bunch of entries, including one for 02:00.0 Ethernet controller (it's an Atheros AR8152 v 1.1 if you're interested) but no wifi controller or anything. 
$iwconfig returns lo and eth0, both with "no wireless extensions."
ndiswrapper is installed.
I installed ndisgtk and it says I have no wireless drivers.
I'm kind of lost and this is a pain, so if you have any ideas I'd appreciate it.

---

### Post by ahallubuntu on 2013-01-29
> **happyturtle said:**
> I just installed ubuntu 12.04, and although I can get online with an ethernet cord, I have no wifi access. 
I've run most of the code provided in [this post]("http://ubuntuforums.org/showthread.php?p=6183681"). I'd be happy to give details,

Yes, please provide the outputs of the commands given in that post.

---

### Post by Bucky Ball on 2013-01-29
Welcome to the forums. Please provide the output of:

```
sudo lshw -C network
```That is a very old thread you have linked to (over four years) and the information given could well be (is probably) obsolete. ndiswrapper is largely superseded. Did you do an update with the cable then check Additional Drivers?

With ndiswrapper installed and the wrong driver you won't have much luck getting anything else to work.

Please provide the output of the command I have provided and that should give us the card and what you have installed for it along with other info.

---

### Post by AngJinhang on 2013-01-29
> **happyturtle said:**
> I just installed ubuntu 12.04, and although I can get online with an ethernet cord, I have no wifi access. 
I've run most of the code provided in [this post]("http://ubuntuforums.org/showthread.php?p=6183681"). I'd be happy to give details, but this is what seems most important to me: 
$lspci gives me a bunch of entries, including one for 02:00.0 Ethernet controller (it's an Atheros AR8152 v 1.1 if you're interested) but no wifi controller or anything. 
$iwconfig returns lo and eth0, both with "no wireless extensions."
ndiswrapper is installed.
I installed ndisgtk and it says I have no wireless drivers.
I'm kind of lost and this is a pain, so if you have any ideas I'd appreciate it.

ok...do you have wifi on your windows? if you have it, boot back into windows to find your wireless card type. then record it down. boot back into ubuntu, and use a ethernet connection to visit linuxwireless.org, and that is a good website to find most of your drivers. find your driver, open a terminal, follow the instructions for ubuntu, reboot and hope your wifi will work!
and also, remove ndiswrapper. i tried it out but it never works and i dont know why. it will also crash with the driver provided on linuxwireless.org. also do a sudo apt-get update before doing anything.

thanks!

---

### Post by Bucky Ball on 2013-01-29
> **AngJinhang said:**
> ok...do you have wifi on your windows? if you have it, boot back into windows to find your wireless card type.

I have already provided a command to find this information and a lot more while in Ubuntu in the post directly above yours. Please read all posts, not just the first one, to avoid repitition. Thanks. ;)

---

### Post by happyturtle on 2013-01-30
sudo lshw -C network:
 *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: c8:0a:a9:65:60:0e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.10.160 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f2000000-f203ffff ioport:6000(size=128)

Also: I did install updates, but the only thing under additional drivers is a graphics driver.

---

### Post by happyturtle on 2013-01-31
Can anyone help me with this problem?

---

### Post by ahallubuntu on 2013-01-31
Please provide the outputs requested from this post:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by happyturtle on 2013-01-31
Okay, here goes:
1) toshiba satellite L645d
2) lspci: 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)

lsusb: Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
and lspci -nn | grep 'Wireless Brand' returns no results...

3)ifconfig: eth0      Link encap:Ethernet  HWaddr c8:0a:a9:65:60:0e  
          inet addr:192.168.10.160  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fe65:600e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45037 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:115643045 (115.6 MB)  TX bytes:4259649 (4.2 MB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:836821 (836.8 KB)  TX bytes:836821 (836.8 KB)
iwconfig: lo        no wireless extensions.

eth0      no wireless extensions.
iwconfig wlan0: wlan0     No such device

4)lsmod: Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
vesafb                 13844  1 
snd_hda_codec_conexant    62358  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
bnep                   18281  2 
snd_seq_midi           13324  0 
rfcomm                 47604  0 
bluetooth             180153  10 bnep,rfcomm
fglrx                3264017  54 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
joydev                 17693  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13791  0 
edac_core              53746  0 
psmouse                97485  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
toshiba_acpi           18582  0 
video                  19596  0 
serio_raw              13211  0 
sparse_keymap          13890  1 toshiba_acpi
parport_pc             32866  0 
shpchp                 37277  0 
ppdev                  17113  0 
mac_hid                13253  0 
wmi                    19256  1 toshiba_acpi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18248  0 
uas                    18180  0 
atl1c                  41718  0 
usb_storage            49198  1 ums_realtek
 lsmod | grep "wlan_module_name" returns no results

5) do you really want all of dmesg it's ******* long

6) you can find the results from this above

7) lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
iwlist scan wlan0: iwlist: unknown command `wlan0' (check 'iwlist --help').

8) iwlist: unknown command `wlan0' (check 'iwlist --help').

9) iwlist: unknown command `wlan0' (check 'iwlist --help').

10)  * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

