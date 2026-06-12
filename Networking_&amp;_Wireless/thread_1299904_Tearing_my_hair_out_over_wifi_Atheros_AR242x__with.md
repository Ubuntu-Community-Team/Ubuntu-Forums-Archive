---
title: "Tearing my hair out over wifi: Atheros AR242x  with Ubuntu 9.04"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by amykate on 2009-10-24
Hi all, I know this is a typical first post, but I'm really stuck.

I have a Toshiba Satellite P200-11R, which I inherited a month ago because I was going away to uni. A few days ago, Vista crashed, and rather than downloading a cracked version and reinstalling, I decided to make a partition for linux and download Ubuntu 9.04 (rather, my boyfriend did so for me, so I'm assuming he did so correctly)

For all of yesterday and this morning, the wifi was working fine (not as well as it had with vista - a bit patchy, kept disconnecting and reconnecting) until about 1 or 2pm today, at which point it wouldn't connect to any wifi network.

At this point I followed the troubleshooting guide, to no avail. Then I tried to physically switch the wireless device off and on again, which didn't help either. Then I activated a driver called "madwifi" and restarted. This seems to have done the most damage, because now when I click on the network manager, the only option it gives me is the Wired Network or VPN connections (there used to be "Wireless Network" as well as a list of the available networks).

So I'm well and truly screwed now. I'm now using my flatmate's pc to try and fix this mess, because, of course, I have no internet connection on my own. I meant to study today, but have spent most of it struggling and fighting with the pc. I don't want to go back to Vista :( so I'll post up as many specs as I can, and if anyone can help, I shall be eternally in their debt!
[B]
Wireless Brand, Model and Wireless Chipset[/B]

$lspci

> 00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
11:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
17:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1d:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1d:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1d:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1d:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller$lsusb

> katie@katie-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1bcf:05c5 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
katie@katie-laptop:~$ **Check interface**

$ifconfig

> katie@katie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:ac:d8:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4056 (4.0 KB)  TX bytes:4056 (4.0 KB)$iwconfig
> 
katie@katie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
**Check for modules**

$lsmod

> katie@katie-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            99648  1 
binfmt_misc            16776  1 
radeon                342816  2 
drm                    96424  3 radeon
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435252  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63368  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
pcmcia                 44748  0 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               41600  1 uvcvideo
tifm_7xx1              13824  0 
soundcore              15200  1 snd
v4l1_compat            21764  2 uvcvideo,videodev
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                61972  0 
ati_agp                14988  0 
tifm_core              15900  1 tifm_7xx1
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_piix4              18448  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
pcspkr                 10496  0 
video                  25872  0 
serio_raw              13444  0 
agpgart                42696  2 drm,ati_agp
k8temp                 12416  0 
output                 11008  1 video
shpchp                 40212  0 
joydev                 18368  0 
input_polldev          11912  0 
ath_pci                99224  0 
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit**Kernel boot messages**
$dmesg

> [    0.608197] pnp: PnP ACPI: found 11 devices
[    0.608199] ACPI: ACPI bus type pnp unregistered
[    0.608203] PnPBIOS: Disabled by ACPI PNP
[    0.608212] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.608216] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.608224] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.608227] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.608230] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.608233] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.608236] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.608238] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.608241] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.608244] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.608247] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.608250] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.608252] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.608255] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.608258] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.608261] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.608264] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.608267] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.608270] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.608272] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.608275] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.608278] system 00:08: ioport range 0xfd60-0xfddf has been reserved
[    0.608285] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.608288] system 00:09: iomem range 0xfff00000-0xffffffff has been reserved
[    0.643030] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.643034] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.643038] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf81fffff
[    0.643042] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.643046] pci 0000:00:05.0: PCI bridge, secondary bus 0000:0b
[    0.643048] pci 0000:00:05.0:   IO window: disabled
[    0.643051] pci 0000:00:05.0:   MEM window: disabled
[    0.643053] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.643058] pci 0000:00:06.0: PCI bridge, secondary bus 0000:11
[    0.643061] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    0.643064] pci 0000:00:06.0:   MEM window: 0xf8300000-0xf83fffff
[    0.643067] pci 0000:00:06.0:   PREFETCH window: 0x0000008c000000-0x0000008c0fffff
[    0.643071] pci 0000:00:07.0: PCI bridge, secondary bus 0000:17
[    0.643073] pci 0000:00:07.0:   IO window: disabled
[    0.643076] pci 0000:00:07.0:   MEM window: 0xf8200000-0xf82fffff
[    0.643079] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.643086] pci 0000:1d:04.0: CardBus bridge, secondary bus 0000:1e
[    0.643088] pci 0000:1d:04.0:   IO window: 0x002000-0x0020ff
[    0.643097] pci 0000:1d:04.0:   IO window: 0x002400-0x0024ff
[    0.643102] pci 0000:1d:04.0:   PREFETCH window: 0x88000000-0x8bffffff
[    0.643108] pci 0000:1d:04.0:   MEM window: 0x90000000-0x93ffffff
[    0.643113] pci 0000:00:14.4: PCI bridge, secondary bus 0000:1d
[    0.643117] pci 0000:00:14.4:   IO window: 0x2000-0x2fff
[    0.643123] pci 0000:00:14.4:   MEM window: 0xf8400000-0xf84fffff
[    0.643127] pci 0000:00:14.4:   PREFETCH window: 0x00000088000000-0x0000008bffffff
[    0.643143] pci 0000:00:05.0: setting latency timer to 64
[    0.643148] pci 0000:00:06.0: setting latency timer to 64
[    0.643153] pci 0000:00:07.0: setting latency timer to 64
[    0.643170] pci 0000:1d:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.643177] bus: 00 index 0 io port: [0x00-0xffff]
[    0.643179] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.643181] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.643184] bus: 01 index 1 mmio: [0xf8000000-0xf81fffff]
[    0.643186] bus: 01 index 2 mmio: [0xf0000000-0xf7ffffff]
[    0.643188] bus: 01 index 3 mmio: [0x0-0x0]
[    0.643190] bus: 0b index 0 mmio: [0x0-0xfff]
[    0.643193] bus: 0b index 1 mmio: [0x0-0xfffff]
[    0.643195] bus: 0b index 2 mmio: [0x0-0x0]
[    0.643197] bus: 0b index 3 mmio: [0x0-0x0]
[    0.643199] bus: 11 index 0 io port: [0xa000-0xafff]
[    0.643201] bus: 11 index 1 mmio: [0xf8300000-0xf83fffff]
[    0.643203] bus: 11 index 2 mmio: [0x8c000000-0x8c0fffff]
[    0.643205] bus: 11 index 3 mmio: [0x0-0x0]
[    0.643207] bus: 17 index 0 mmio: [0x0-0x0]
[    0.643210] bus: 17 index 1 mmio: [0xf8200000-0xf82fffff]
[    0.643212] bus: 17 index 2 mmio: [0x0-0x0]
[    0.643214] bus: 17 index 3 mmio: [0x0-0x0]
[    0.643216] bus: 1d index 0 io port: [0x2000-0x2fff]Network Configuration

> katie@katie-laptop:~$ sudo lshw -C network
[sudo] password for katie: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:11:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:ac:d8:54
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:8a:97:08:a3:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes**Scan for networks**

> katie@katie-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
**Kernal/architecture: **
2.6.28-16-generic i686

Lastly, I ran $ sudo/etc/init.d/networking restart in the terminal, which just said

*Reconfiguring network interfaces... [OK]

Sorry to be a pain, many thanks again!

Amy Kate

---

### Post by drpjkurian on 2009-10-25
Hi Amy
I am very sorry to hear that your wifi has gone.  

Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)
It might help you
 
You can also install latest Ubuntu which is code named as Karmic Koala It will be released on 29th 0ctober.

Wish you the best

With regards
Dr Kurian

---

### Post by ken_do_san on 2009-10-25
Hi Amy

I had the same problem with my laptop with the same atheros, try this link and follow the instructions, it worked or me (except the wireless led doesn't light up, but thats no great problem).

Hope it works for you as well.

Cheers

---

### Post by ken_do_san on 2009-10-25
Oh yeah best give you the link :)

[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

---

### Post by wilee-nilee on 2009-10-25
If you cannot get it fixed with the links and you can plug in etho just install wicd in synaptic and restart and a new icon will show in the notification area that is click-able like the network manager. Wicd is a excellent substitute for network manager.

---

