---
title: "Please help !!!wireless connectivity lost after upgrade/ update"
date: 2012-09-21
forum: Networking &amp; Wireless
---

### Post by parvas24 on 2012-09-21
Iam a newbie to Ubuntu and linux .... 

I had install Ubuntu 12.04.1 precise pangolin LTS last month

Had no problems with connectivity , both wired and wireless connections worked ... until recently I happened to install and upgrade the Ubuntu repositories... after restart the wired connection works but my** wireless connection is lost completel**y ... I use a wireless router at home .. all my other wireless devices can pick up and connect to the internet through the router well ....** I now only use wired connection.... I wonder how can upgrading the Ubuntu software using terminal destroy wireless conenction after reboot??? **

My computer specs :
COMPAQ B2800 laptop
Intel PRO wireless 3945 network adapter.
Ubuntu version 12.04.1 LTS
                                  3.2.0-29-generic-pae i686




                                   
COMPAQ B2800 laptop
 Intel 3945 wireless adapter
 Intel Corporation 82801 Mobile PCI Bridge (rev d4)
 eth0      Link encap:Ethernet  HWaddr 00:16:35:36:08:1d   
           inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::216:35ff:fe36:81d/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:1742 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:1852 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:1319490 (1.3 MB)  TX bytes:224253 (224.2 KB) 
           Interrupt:20 Base address:0xd800  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:358 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:358 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:42265 (42.2 KB)  TX bytes:42265 (42.2 KB) 
 

  

                                   
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces 
  * Reconfiguring network interfaces...


                                   
*-network                
        description: Ethernet interface 
        product: RTL-8139/8139C/8139C+ 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 4 
        bus info: pci@0000:02:04.0 
        logical name: eth0 
        version: 10 
        serial: 00:16:35:36:08:1d 
        size: 100Mbit/s 
        capacity: 100Mbit/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s 
        resources: irq:20 ioport:d800(size=256) memory:feaff000-feaff0ff 
 





                                   
Module                  Size  Used by 
 iwl3945                73152  0  
 iwl_legacy             71134  1 iwl3945 
 mac80211              436455  2 iwl3945,iwl_legacy 
 cfg80211              178679  3 iwl3945,iwl_legacy,mac80211 
 usb_storage            39646  1  
 joydev                 17393  0  
 snd_hda_codec_analog    75395  1  
 snd_hda_intel          32765  2  
 snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel 
 snd_hwdep              13276  1 snd_hda_codec 
 rfcomm                 38139  12  
 snd_pcm                80845  2 snd_hda_intel,snd_hda_codec 
 snd_seq_midi           13132  0  
 snd_rawmidi            25424  1 snd_seq_midi 
 radeon                737789  3  
 pcmcia                 39791  0  
 psmouse                72919  0  
 snd_seq_midi_event     14475  1 snd_seq_midi 
 btusb                  17912  1  
 serio_raw              13027  0  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
 r592                   17808  0  
 bnep                   17830  2  
 parport_pc             32114  0  
 r852                   17901  0  
 sm_common              16737  1 r852 
 nand                   49667  2 r852,sm_common 
 nand_ids                8547  1 nand 
 mtd                    35584  2 sm_common,nand 
 nand_bch               13003  1 nand 
 bch                    21757  1 nand_bch 
 yenta_socket           27465  0  
 pcmcia_rsrc            18367  1 yenta_socket 
 bluetooth             158438  23 rfcomm,btusb,bnep 
 ppdev                  12849  0  
 ttm                    65344  1 radeon 
 drm_kms_helper         45466  1 radeon 
 nand_ecc               13070  1 nand 
 snd_timer              28931  2 snd_pcm,snd_seq 
 memstick               15857  1 r592 
 binfmt_misc            17292  1  
 asus_laptop            23693  0  
 sparse_keymap          13658  1 asus_laptop 
 pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
 drm                   197692  5 radeon,ttm,drm_kms_helper 
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
 input_polldev          13648  1 asus_laptop 
 video                  19068  0  
 snd                    62064  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 mac_hid                13077  0  
 soundcore              14635  1 snd 
 snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
 i2c_algo_bit           13199  1 radeon 
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp 
 firewire_ohci          40172  0  
 sdhci_pci              18324  0  
 8139too                23283  0  
 8139cp                 26759  0  
 sdhci                  28241  1 sdhci_pci 
 firewire_core          56906  1 firewire_ohci 
 crc_itu_t              12627  1 firewire_core
 

 dmesg
  1.187337] udevd[87]: starting version 175 
 [    1.359773] sdhci: Secure Digital Host Controller Interface driver 
 [    1.359777] sdhci: Copyright(c) Pierre Ossman 
 [    1.378491] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
 [    1.378520] 8139cp 0000:02:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too 
 [    1.379008] 8139too: 8139too Fast Ethernet driver 0.9.28 
 [    1.379056] 8139too 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [    1.384057] usb 2-1: new full-speed USB device number 2 using uhci_hcd 
 [    1.386190] 8139too 0000:02:04.0: eth0: RealTek RTL8139 at 0xd800, 00:16:35:36:08:1d, IRQ 20 
 [    1.386210] sdhci-pci 0000:02:03.2: SDHCI controller found [1180:0822] (rev 17) 
 [    1.386228] sdhci-pci 0000:02:03.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20 
 [    1.387248] sdhci-pci 0000:02:03.2: Will use DMA mode even though HW doesn't fully claim to support it. 





   
                                     dmesg
  1.187337] udevd[87]: starting version 175 
 [    1.359773] sdhci: Secure Digital Host Controller Interface driver 
 [    1.359777] sdhci: Copyright(c) Pierre Ossman 
 [    1.378491] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
 [    1.378520] 8139cp 0000:02:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too 
 [    1.379008] 8139too: 8139too Fast Ethernet driver 0.9.28 
 [    1.379056] 8139too 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [    1.384057] usb 2-1: new full-speed USB device number 2 using uhci_hcd 
 [    1.386190] 8139too 0000:02:04.0: eth0: RealTek RTL8139 at 0xd800, 00:16:35:36:08:1d, IRQ 20 
 [    1.386210] sdhci-pci 0000:02:03.2: SDHCI controller found [1180:0822] (rev 17) 
 [    1.386228] sdhci-pci 0000:02:03.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20 
 [    1.387248] sdhci-pci 0000:02:03.2: Will use DMA mode even though HW doesn't fully claim to support it. 
 [    1.387277] mmc0: no vmmc regulator found 
 [    1.388312] Registered led device: mmc0:: 
 [    1.398845] mmc0: SDHCI controller on PCI [0000:02:03.2] using DMA 
 [    1.398890] firewire_ohci 0000:02:03.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22 
 [    1.461930] firewire_ohci: Added fw-ohci device 0000:02:03.1, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x11 
 [    1.726696] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null) 
 [    1.960147] firewire_core: created device fw0: GUID 0060b000001ae0f1, S400 
 [   22.010726] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   22.046648] udevd[310]: starting version 175 
 [   22.124447] Adding 511996k swap on /dev/sda2.  Priority:-1 extents:1 across:511996k  
 [   22.141191] lp: driver loaded but no devices found 
 [   22.309421] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro 
 [   22.313059] intel_rng: FWH not detected 
 [   22.486341] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input4 
 [   22.493333] asus_laptop: Asus Laptop Support version 0.42 
 [   22.493493] asus_laptop:   B2800 model detected 
 [   22.493939] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
 [   22.526439] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5 
 [   22.542742] [drm] Initialized drm 1.1.0 20060810 
 [   22.676165] Registered led device: asus::mail 
 [   22.676243] Registered led device: asus::touchpad 
 [   22.678002] yenta_cardbus 0000:02:03.0: CardBus bridge found [103c:30af] 
 [   22.686757] Bluetooth: Core ver 2.16 
 [   22.686777] NET: Registered protocol family 31 
 [   22.686780] Bluetooth: HCI device and connection manager initialized 
 [   22.686784] Bluetooth: HCI socket layer initialized 
 [   22.686786] Bluetooth: L2CAP socket layer initialized 
 [   22.686792] Bluetooth: SCO socket layer initialized 
 [   22.692440] ppdev: user-space parallel port driver 
 [   22.706120] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 [   22.706125] Bluetooth: BNEP filters: protocol multicast 
 [   22.734981] type=1400 audit(1348248067.212:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=609 comm="apparmor_parser" 
 [   22.736710] type=1400 audit(1348248067.216:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=609 comm="apparmor_parser" 
 [   22.804835] yenta_cardbus 0000:02:03.0: ISA IRQ mask 0x0cb8, PCI irq 21 
 [   22.804841] yenta_cardbus 0000:02:03.0: Socket status: 30000006 
 [   22.804846] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06 
 [   22.804857] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge window: [io  0xd000-0xdfff] 
 [   22.804861] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xdfff: excluding 0xd000-0xd0ff 0xd400-0xd4ff 0xd800-0xd8ff 
 [   22.808643] Bluetooth: Generic Bluetooth USB driver ver 0.6 
 [   22.821285] type=1400 audit(1348248067.300:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=621 comm="apparmor_parser" 
 [   22.826209] type=1400 audit(1348248067.304:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=621 comm="apparmor_parser" 
 [   22.826545] type=1400 audit(1348248067.304:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=621 comm="apparmor_parser" 
 [   22.853877]  
 [   22.853885] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge window: [mem 0xfea00000-0xfeafffff] 
 [   22.853891] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfea00000-0xfeafffff: excluding 0xfeaf0000-0xfeafffff 
 [   22.853907] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge window: [mem 0x60000000-0x63ffffff pref] 
 [   22.853910] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x63ffffff: excluding 0x60000000-0x63ffffff 
 [   22.859647] usbcore: registered new interface driver btusb 
 [   22.873704] r592 0000:02:03.3: PCI INT C -> GSI 20 (level, low) -> IRQ 20 
 [   22.873715] r592 0000:02:03.3: setting latency timer to 64 
 [   22.876934] r592: driver successfully loaded 
 [   22.877012] r852 0000:02:03.4: PCI INT C -> GSI 20 (level, low) -> IRQ 20 
 [   22.877021] r852 0000:02:03.4: setting latency timer to 64 
 [   22.881923] r852: Non dma capable device detected, dma disabled 
 [   22.881938] r852: driver loaded successfully 
 [   22.886812] [drm] radeon defaulting to kernel modesetting. 
 [   22.886817] [drm] radeon kernel modesetting enabled. 
 [   22.886889] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   22.886895] radeon 0000:01:00.0: setting latency timer to 64 
 [   22.898217] [drm] initializing kernel modesetting (RV380 0x1002:0x5462 0x103C:0x30AF). 
 [   22.898249] [drm] register mmio base: 0xFE9F0000 
 [   22.898251] [drm] register mmio size: 65536 
 [   22.898408] [drm] Generation 2 PCI interface, using max accessible memory 
 [   22.898416] radeon 0000:01:00.0: VRAM: 128M 0x00000000D0000000 - 0x00000000D7FFFFFF (128M used) 
 [   22.898420] radeon 0000:01:00.0: GTT: 512M 0x00000000B0000000 - 0x00000000CFFFFFFF 
 [   22.898433] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010). 
 [   22.898435] [drm] Driver supports precise vblank timestamp query. 
 [   22.898481] radeon 0000:01:00.0: irq 41 for MSI/MSI-X 
 [   22.898487] radeon 0000:01:00.0: radeon: using MSI. 
 [   22.898514] [drm] radeon: irq initialized. 
 [   22.905056] [drm] Detected VRAM RAM=128M, BAR=128M 
 [   22.905061] [drm] RAM width 128bits DDR 
 [   22.910367] [TTM] Zone  kernel: Available graphics memory: 442012 kiB. 
 [   22.910372] [TTM] Zone highmem: Available graphics memory: 771616 kiB. 
 [   22.910374] [TTM] Initializing pool allocator. 
 [   22.910404] [drm] radeon: 128M of VRAM memory ready 
 [   22.910406] [drm] radeon: 512M of GTT memory ready. 
 [   22.910425] [drm] GART: num cpu pages 131072, num gpu pages 131072 
 [   22.911523] [drm] radeon: 1 quad pipes, 1 Z pipes initialized. 
 [   22.913237] [drm] PCIE GART of 512M enabled (table at 0x00000000D0040000). 
 [   22.926653] radeon 0000:01:00.0: WB enabled 
 [   22.928883] [drm] Loading R300 Microcode 
 [   23.214724] init: failsafe main process (693) killed by TERM signal 
 [   23.245159] Bluetooth: RFCOMM TTY layer initialized 
 [   23.245166] Bluetooth: RFCOMM socket layer initialized 
 [   23.245169] Bluetooth: RFCOMM ver 1.11 
 [   23.309003] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   23.309071] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X

---

