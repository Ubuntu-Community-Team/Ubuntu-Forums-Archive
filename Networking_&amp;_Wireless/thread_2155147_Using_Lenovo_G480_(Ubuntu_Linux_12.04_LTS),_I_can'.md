---
title: "Using Lenovo G480 (Ubuntu Linux 12.04 LTS), I can't connect to my wifi."
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by psychephia on 2013-06-17
Hi,
[SIZE=4]
[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=4]I'm using Lenovo G480 and I just installed Ubuntu Linux 12.04 LTS yesterday (dual booting it with Windows 7). I cannot connect to my wifi. I'm a newbie to Linux and I have no idea how to fix this. Can someone help?

here are the codes below:[/SIZE]

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]lspci:[/FONT][/COLOR]

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1058 (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
[COLOR=#333333][FONT=UbuntuRegular]
sudo lshw -C network[/FONT][/COLOR]
*-network                  description: Network controller
   product: BCM4313 802.11b/g/n Wireless LAN Controller
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:03:00.0 
  version: 01
   width: 64 bits
   clock: 33MHz 
  capabilities: pm msi pciexpress bus_master cap_list
   configuration: driver=bcma-pci-bridge latency=0 
  resources: irq:17 memory:eb500000-eb503fff
*-network   description: Ethernet interface 
  product: AR8162 Fast Ethernet 
  vendor: Atheros Communications Inc.
   physical id: 0 
  bus info: pci@0000:04:00.0
   logical name: eth0 
  version: 10 
  serial: 3c:97:0e:19:f2:bf 
  capacity: 100Mbit/s 
  width: 64 bits 
  clock: 33MHz
   capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
  configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair   resources: irq:19 memory:eb400000-eb43ffff ioport:2000(size=128)
*-network   description: Wireless interface
   physical id: 3
   logical name: wlan0
   serial: 08:ed:b9:a5:9b:a1
   capabilities: ethernet physical wireless 
  configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-34-generic firmware=N/A ip=192.168.254.101 link=yes multicast=yes wireless=IEEE 802.11bgn
[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]Module                        Size  Used by
nls_utf8                       12558  1 
isofs                            40307  1 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
joydev                          17694  0 
rfcomm                          47562  0 
bnep                             18240  2 
parport_pc                     32867  0 
ppdev                           17114  0 
lp                                 17800  0 
parport                          46563  3 parport_pc,ppdev,lp
coretemp                       13642  0 
kvm                              422160  0 
ghash_clmulni_intel          13221  0 
arc4                              12530  2 
aesni_intel                      51134  2 
cryptd                            20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64                    17256  1 aesni_intel
brcmsmac                      541775  0 
mac80211                      555272  1 brcmsmac
brcmutil                         14756  1 brcmsmac
cfg80211                       208382  2 brcmsmac,mac80211
cordic                           12575  1 brcmsmac
snd_hda_intel                 34063  3 
snd_hda_codec              135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep                    17765  1 snd_hda_codec
snd_pcm                       97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi                  13325  0 
snd_rawmidi                  30750  1 snd_seq_midi
snd_seq_midi_event       14900  1 snd_seq_midi
snd_seq                      61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer                   29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                       22432  0 
bluetooth                211812  14 rfcomm,bnep,btusb
alx                       73500  0 
uvcvideo               78117  0 
mdio                     13808  1 alx
videobuf2_core         33025  1 uvcvideo
videodev               125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
microcode              23030  0 
snd                      83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse               102506  0 
serio_raw              13216  0 
lpc_ich                17145  0 
bcma                   35762  1 brcmsmac
mei                      41410  0 
ideapad_laptop       18235  0 
soundcore              15092  1 snd
snd_page_alloc        18573  2 snd_hda_intel,snd_pcm
sparse_keymap        13891  1 ideapad_laptop
nouveau                 924024  1 
ttm                       88495  1 nouveau
mxm_wmi              13022  1 nouveau
mac_hid                13254  0 
wmi                     19257  2 nouveau,mxm_wmi
i915                    535221  3 
drm_kms_helper    49259  2 nouveau,i915
drm                    290059  7 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit          13565  2 nouveau,i915
video                  19653  2 nouveau,i915
usb_storage         49288  0 
ahci                   25869  2 
libahci                27338  1 ahci
[COLOR=#333333][FONT=UbuntuRegular]

Thanks. Your help would be greatly appreciated. God bless :)


[/FONT][/COLOR]

---

### Post by Hadaka on 2013-06-17
Hi, give this a go..
```
sudo su
apt-get install brcmwl-kernel-source
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
modprobe -r brcmsmac
modprobe wl
exit 0
```

---

### Post by psychephia on 2013-06-17
This is what it said after typing the commands above:


sudo su
apt-get install brcmwl-kernel-source
reading package list... done
Building dependency tree
Reading state information... done
E: Unable to locate package brcmwl-kernel-source
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
modprobe -r brcmsmac
modprobe wl
FATAL: module wl not found
exit 0 


Hi, what to do next?
After I've done this command, I couldn't find any wireless network option under the wireless menu. Pls help. Thank you.

---

### Post by Hadaka on 2013-06-17
Hi,did you do those commands from a wired connection?
if not..please connect the wire and do them again
thanks.

---

### Post by chili555 on 2013-06-17
I think my colleague Hadaka might have made a typo. Please try:```
sudo apt-get install** bcmwl**-kernel-source
```In other words, without an R.

I actually think brcmsmac is correct, but let's just find out!

---

### Post by sebaogal on 2013-07-13
Hi, i'm in the same situation: same laptop, but with Linux Mint 15, in other words, Ubuntu Raring. I could not see the available networks. After doing the procedure that Hadaka told us i'm able to see available networks, but i can't connect to any. I click in one, put the key, wait wait wait and nothing, it retries. Any help please?

---

### Post by chili555 on 2013-07-13
> **sebaogal said:**
> Hi, i'm in the same situation: same laptop, but with Linux Mint 15, in other words, Ubuntu Raring. I could not see the available networks. After doing the procedure that Hadaka told us i'm able to see available networks, but i can't connect to any. I click in one, put the key, wait wait wait and nothing, it retries. Any help please?And the exact same hardware?```
lspci -nn | grep 0280
```

---

### Post by bozo_the_grey on 2013-07-13
Hi,

I have the same problem since the last ubuntu update (admittedly I don't know exactly what was updated). 

I am running 12.04 LTS on Lenovo Ideapad S12 (nvidia ion) in dual boot with windows7.

lspci -nn | grep 0280
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)


Same as the other users: Ubuntu sees many wireless connections, but not my own.
I have rencently set a fixed ip address to the laptop from the router. I might try to take that off.

I have blacklisted brcmsmac and bcma. 
bcmwl-kernel-source was already the latest.

lspci:

00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:0d.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:0e.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: NVIDIA Corporation ION VGA [GeForce 9400M] (rev b1)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

sudo lshw -C network &
[1] 2355
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:2d:59:e0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v3.04 ip=192.168.1.64 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:c2000000-c200ffff
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:31:b9:20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:c2200000-c2203fff

---

### Post by bozo_the_grey on 2013-07-13
## SOLVED ## 
- moved router channel from 13 to 3
- disconnect from wired network (this probably triggered a refresh of the list of wireless connections available)
- my connection was visible and I managed to connect to it
- definitely a bug that was already spotted [http://askubuntu.com/questions/138492/my-wireless-network-not-visible-in-wireless-network-list-with-a-broadcom-card]("http://askubuntu.com/questions/138492/my-wireless-network-not-visible-in-wireless-network-list-with-a-broadcom-card")

---

### Post by sebaogal on 2013-07-16
> **chili555 said:**
> And the exact same hardware?```
lspci -nn | grep 0280
```

Exactly the same:

```
saogalde@lenovolinux$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

I would be so happy if i could fix this :(

---

### Post by chili555 on 2013-07-16
> **sebaogal said:**
> Exactly the same:

```
saogalde@lenovolinux$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

I would be so happy if i could fix this :(Allow me to pursue my brcmsmac theory, if you will. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe brcmsmac
```Any improvement? It may take a reboot.

---

### Post by sebaogal on 2013-07-16
My friend, i have followed your suggestions, but it only made the conections undetectable. I fixed my connection by installing the propietary drivers downloaded directly from Broadcom and followed carefully the README [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt).

I have modified the line 388 in src/wl/wl_linux.c:
```


 .ndo_set_multicast_list = wl_set_multicast_list,

to

 .ndo_set_rx_mode = wl_set_multicast_list,


```

Then "make" and followed the "Fresh Installation" instructions in the README. I have blacklisted these:

```
blacklist ssb
blacklist bcma
blacklist b43
blacklist brcmsmac

```
My lsmod now shows:
```
lenovolinux saogalde # lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17390  0 
wl                   2573568  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
wmi                    19256  0 
psmouse                87603  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
i915                  468651  2 
drm_kms_helper         46978  1 i915
mac_hid                13253  0 
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
alx                    67934  0 
compat                 13227  1 alx
mdio                   13770  1 alx
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18027  0 
usb_storage            49198  0 


```
And lspci -vv
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Broadcom Corporation Device 0587
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <4us, L1 <64us
            ClockPM+ Surprise- LLActRep+ BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [13c v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Capabilities: [160 v1] Device Serial Number 00-00-3d-ff-ff-c8-c0-14
    Capabilities: [16c v1] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: bcma, brcmsmac
```

At first reboot it did not work, so i did "insmod wl.ko" **again**, and suddenly worked. It seems the connection speed is not as fast as the wired, i will be reporting more. I have read in many forums that brcmsmac driver does not work for this card. Damn 4313 haha. Clearly the wl driver available in the repos is broken and need to be fixed. Please developers! :KS

I'm grateful with you :D

---

### Post by chili555 on 2013-07-16
Glad it's working by whatever means.

---

