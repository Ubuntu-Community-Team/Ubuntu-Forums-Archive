---
title: "no wireless or ethernet on precise upgrade"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by bobmounger on 2012-04-28
last night I ran the upgrade to 12.04 from 11.10. Now neither the ethernet or wireless works. 

This laptop has nforce nvidia ethernet & broadcom wireless


What did I do wrong?
~~~~~~~~~~~~~

Module                  Size  Used by
cdc_ether              13312  0 
usbnet                 25214  1 cdc_ether
cdc_acm                22306  0 
usb_storage            39646  0 
snd_hrtimer            12648  1 
joydev                 17393  0 
vesafb                 13516  1 
snd_hda_codec_conexant    52365  1 
nvidia              10962290  33 
parport_pc             32114  0 
rfcomm                 38139  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67203  0 
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
videodev               86588  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
hp_wmi                 13652  0 
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13658  1 hp_wmi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
psmouse                72919  0 
serio_raw              13027  0 
k8temp                 12905  0 
soundcore              14635  1 snd
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mtd                    35584  2 sm_common,nand
r592                   17808  0 
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
memstick               15857  1 r592
wmi                    18744  1 hp_wmi
i2c_nforce2            12906  0 
mac_hid                13077  0 
video                  19068  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_amd               13750  0 
forcedeth              58096  0 


00:00.0 RAM memory: NVIDIA Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: NVIDIA Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP65 SMU (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP65 USB Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: NVIDIA Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: NVIDIA Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: NVIDIA Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: NVIDIA Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: NVIDIA Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
05:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


eth0      Link encap:Ethernet  HWaddr 00:1e:68:41:1e:ae  
          inet6 addr: fe80::21e:68ff:fe41:1eae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7666 (7.6 KB)  TX bytes:49304 (49.3 KB)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:580760 (580.7 KB)  TX bytes:580760 (580.7 KB)

---

### Post by chili555 on 2012-04-28
Let's start with wireless. Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by bobmounger on 2012-04-28
lspci:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)

rfkill:
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


Thanks,

bob

---

### Post by chili555 on 2012-04-28
Actually, to get wireless going we need to download and install some packages, a task that will be much easier with ethernet. Your ethernet actually looks pretty healthy. You have a driver, forcedeth, and a wireless interface eth0. It even looks like it *has* been connected:> eth0 Link encap:Ethernet HWaddr 00:1e:68:41:1e:ae
inet6 addr: fe80::21e:68ff:fe41:1eae/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:62 errors:0 dropped:0 overruns:0 frame:0
TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
[COLOR="Red"]RX bytes:7666[/COLOR] (7.6 KB) [COLOR="Red"]TX bytes:49304[/COLOR] (49.3 KB)
Interrupt:20 Base address:0x8000When you hook up the ethernet cable, does it try? What are the symptoms? If you manage to get an ethernet connection, open a terminal and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Your wireless should be working then.

---

### Post by bobmounger on 2012-04-28
ethernet doesn't work. At one point I tried usb tethering an android phone to the laptop, & it seemed to make a connection. perhaps that is what you are seeing? 

When I hook up an ethernet cable the antenna icon shimmers & the text "requesting a wired network address for wired connection 1"
appears. eventually it gives up & says wired disconnected & a graphic of an ethernet jack with a red x on it appears



thanks, 
bob

---

### Post by chili555 on 2012-04-28
Let's see if there are any interesting messages here:```
dmesg | grep eth
```Thanks.> "requesting a wired network address for wired connection 1"
appears. eventually it gives up & says wired disconnected & a graphic of an ethernet jack with a red x on it appearsSo it is trying. Have you made any settings in Network Manager? Usually, NM will do all the work and human intervention is not needed. If you have added any settings, please delete them.

The suite of packages needed for wireless is quite large; if we can coax ethernet to life, we'll save a lot of time and trouble.

---

### Post by bobmounger on 2012-04-28
when I tried to do usb tethering to run install --reinstall ...

I see
E: Unable to locate package bcmwl-kernal-source

tethering seems to give me a connection.

---

### Post by bobmounger on 2012-04-28
I definitely connect with usb tethering

dmesg:
[    0.199665] i2c-core: driver [aat2870] using legacy suspend method
[    0.199667] i2c-core: driver [aat2870] using legacy resume method
[    0.222123] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f7425900), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    0.222137] ACPI Error: Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f7425900), AE_AML_BUFFER_LIMIT (20110623/uteval-103)
[    1.340829] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.341006] forcedeth 0000:00:06.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.341012] forcedeth 0000:00:06.0: setting latency timer to 64
[    1.865119] forcedeth 0000:00:06.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:41:1e:ae
[    1.865125] forcedeth 0000:00:06.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[   15.467587] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.905346] forcedeth 0000:00:06.0: eth0: no link during initialization
[   16.906016] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.906604] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1515.324485] forcedeth 0000:00:06.0: eth0: link up
[ 1515.325669] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1526.288054] eth0: no IPv6 routers present
[ 1556.240069] eth0: no IPv6 routers present
[ 1604.600080] eth0: no IPv6 routers present
[ 1652.960067] eth0: no IPv6 routers present
[ 1700.208078] eth0: no IPv6 routers present
[ 2045.576068] eth0: no IPv6 routers present
[ 2093.680060] eth0: no IPv6 routers present
[ 2141.120053] eth0: no IPv6 routers present
[ 2189.328061] eth0: no IPv6 routers present
[ 2308.335279] forcedeth 0000:00:06.0: eth0: link down
[ 2370.478107] cdc_ether 1-6:1.1: usb0: register 'cdc_ether' at usb-0000:00:02.1-6, CDC Ethernet Device, a2:60:45:d8:3f:a3
[ 2370.478480] usbcore: registered new interface driver cdc_ether
[ 3117.494059] cdc_ether 1-6:1.1: usb0: unregister 'cdc_ether' usb-0000:00:02.1-6, CDC Ethernet Device
[ 3148.897848] forcedeth 0000:00:06.0: eth0: link up
[ 3159.536061] eth0: no IPv6 routers present

---

### Post by chili555 on 2012-04-28
> E: Unable to locate package bcmwl-kernal-sourceI assume you actually typed bcmwl-kern[COLOR="Red"]e[/COLOR]l-source. Perhaps it's not already installed. Please try:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by bobmounger on 2012-04-28
Sorry I forgot to answer your question. No, I have not changed or even touched anything in the network manager

---

### Post by bobmounger on 2012-04-28
so sorry fat fingers.


reading package lists... Done

bcmwl-kernel-source is already the newest version.
0 upgraded 0 newly installed 0 to remove and 1 not upgraded.

sudo modprobe wl
FATAL: Module wl not found.

---

### Post by chili555 on 2012-04-28
> [ 1515.324485] forcedeth 0000:00:06.0: eth0: link up
[ 1515.325669] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1526.288054] eth0: no IPv6 routers presentLooks typical of a perfectly operating ethernet connection. I see nothing wrong to try to fix so far.> bcmwl-kernel-source is already the newest version.
0 upgraded 0 newly installed 0 to remove and 1 not upgraded.

sudo modprobe wl
FATAL: Module wl not found.That suggests it *is* installed but not correctly. Please try again with the --reinstall part. Either copy and paste from above or proofread carefully.

---

### Post by bobmounger on 2012-04-28
Solved!!! that fixed it. 

Thank You so much for your help & especially your patience.

---

### Post by chili555 on 2012-04-28
Very happy to have helped and I'm glad it's fixed. Have fun!

---

