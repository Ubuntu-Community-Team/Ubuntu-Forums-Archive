---
title: "D-Link DWA 130 Rev C on Ubuntu 9.10"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by JohnDoeKyrgyz on 2009-11-19
Hello,

I'm wondering if anyone has been able to get a D-Link DWA 130 Rev C on Ubuntu 9.10. I have tried pretty much everything I can think of. Compiling the drivers provided on the DLink site gives the following errors:

```

john@John:~/Downloads/rtl8192u_linux_2.6.0006.1031.2008$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.o                                                                             
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.c: In function ‘RxReorderIndicatePacket’:                                               
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_rx.c:794: warning: the frame size of 1072 bytes is larger than 1024 bytes                  
  CC [M]  /home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_softmac.o                                                                        
  CC [M]  /home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_tx.o
  CC [M]  /home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_wx.o
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_get_encode_ext_rsl’:
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_wx.c:846: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie_rsl’:
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_wx.c:990: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.o
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rsl’:
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.c:308: warning: comparison of distinct pointer types lacks a cast
make[2]: *** [/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/john/Downloads/rtl8192u_linux_2.6.0006.1031.2008/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
```

I suspect that the source for this driver is incompatible with kernel 2.6.31-14.

When ndiswrapper is loaded, the driver fails to work:

```

[    1.418919] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.418936] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    1.472071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.590038] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    1.837154] usb 2-3: configuration #1 chosen from 1 choice
[    1.871114] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:7f:52:21
[    1.871119] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    2.586063] PM: Starting manual resume from disk
[    2.586068] PM: Resume from partition 8:5
[    2.586069] PM: Checking hibernation image.
[    2.586283] PM: Resume from disk failed.
[    2.608735] EXT4-fs (sda1): barriers enabled
[    2.628260] kjournald2 starting: pid 425, dev sda1:8, commit interval 5 seconds
[    2.628284] EXT4-fs (sda1): delayed allocation enabled
[    2.628287] EXT4-fs: file extents enabled
[    2.636561] EXT4-fs: mballoc enabled
[    2.636579] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.790786] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc000bc209f00]
[    3.402144] type=1505 audit(1258589605.897:2): operation="profile_load" pid=448 name=/sbin/dhclient3
[    3.402440] type=1505 audit(1258589605.897:3): operation="profile_load" pid=448 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.402627] type=1505 audit(1258589605.897:4): operation="profile_load" pid=448 name=/usr/lib/connman/scripts/dhclient-script
[    3.481020] type=1505 audit(1258589605.969:5): operation="profile_load" pid=450 name=/usr/lib/cups/backend/cups-pdf
[    3.481387] type=1505 audit(1258589605.969:6): operation="profile_load" pid=450 name=/usr/sbin/cupsd
[    3.483866] type=1505 audit(1258589605.979:7): operation="profile_load" pid=451 name=/usr/sbin/mysqld-akonadi
[    3.486078] type=1505 audit(1258589605.979:8): operation="profile_load" pid=452 name=/usr/sbin/tcpdump
[    4.694441] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k 
[    5.126812] udev: starting version 147
[    6.730349] EXT4-fs (sda1): internal journal on sda1:8
[    7.053984] nvidia: module license 'NVIDIA' taints kernel.
[    7.053988] Disabling lock debugging due to kernel taint
[    7.080083] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    7.080996] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[    7.081019] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[    7.311208] nvidia 0000:00:05.0: power state changed by ACPI to D0
[    7.311540] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[    7.311545]   alloc irq_desc for 18 on node 0
[    7.311547]   alloc kstat_irqs on node 0
[    7.311559] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[    7.311566] nvidia 0000:00:05.0: setting latency timer to 64
[    7.311804] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[    7.876501] EDAC MC: Ver: 2.1.0 Oct 16 2009
[    7.876854] ricoh-mmc: Ricoh MMC Controller disabling driver
[    7.876856] ricoh-mmc: Copyright(c) Philip Langdale
[    7.878573] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    7.878710] usbcore: registered new interface driver btusb
[    7.881508] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[    7.881530] ricoh-mmc: Controller is now disabled.
[    8.214661] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.218360] lp: driver loaded but no devices found
[    8.517731] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[    8.518572] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    8.518579] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    8.518582] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    8.518584]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    8.518585]     Might be a BIOS bug, if BIOS says ECC is enabled
[    8.518586]     Use of the override can cause unknown side effects.
[    8.518607] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.669722] sdhci: Secure Digital Host Controller Interface driver
[    8.669725] sdhci: Copyright(c) Pierre Ossman
[    8.827271] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[    8.827642] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    8.827657] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[    8.829759] Registered led device: mmc0::
[    8.829808] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[    9.221867] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[    9.237136] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    9.237143]   alloc irq_desc for 21 on node 0
[    9.237145]   alloc kstat_irqs on node 0
[    9.237157] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[    9.237207] HDA Intel 0000:00:10.1: setting latency timer to 64
[    9.290000] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   10.550554] type=1505 audit(1258614813.047:9): operation="profile_replace" pid=871 name=/sbin/dhclient3
[   10.550858] type=1505 audit(1258614813.047:10): operation="profile_replace" pid=871 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.551031] type=1505 audit(1258614813.047:11): operation="profile_replace" pid=871 name=/usr/lib/connman/scripts/dhclient-script
[   10.554665] type=1505 audit(1258614813.047:12): operation="profile_replace" pid=873 name=/usr/lib/cups/backend/cups-pdf
[   10.555035] type=1505 audit(1258614813.047:13): operation="profile_replace" pid=873 name=/usr/sbin/cupsd
[   10.557235] type=1505 audit(1258614813.047:14): operation="profile_replace" pid=874 name=/usr/sbin/mysqld-akonadi
[   10.559178] type=1505 audit(1258614813.047:15): operation="profile_replace" pid=875 name=/usr/sbin/tcpdump
[   14.006916] usplash:388 freeing invalid memtype ffffffffc0000000-ffffffffc4000000
[   16.742543] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.742546] Bluetooth: BNEP filters: protocol multicast
[   16.799102] Bridge firewalling registered
[   17.312113] ppdev: user-space parallel port driver
[   22.342519] eth0: no IPv6 routers present
[   35.002527] Clocksource tsc unstable (delta = -93354919 ns)
[  333.070050] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  333.228372] usb 1-1: configuration #1 chosen from 1 choice
[  333.278202] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  333.520455] usb 1-1: reset high speed USB device using ehci_hcd and address 3
[  333.671206] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  333.671234] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  333.671258] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  333.671278] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  333.671296] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  333.671315] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  333.671334] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  333.671354] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  333.671437] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  333.671474] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  333.671520] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  333.671560] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  333.671578] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  333.671596] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  333.671647] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  333.671666] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  333.671686] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  333.671704] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  333.671719] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  333.671734] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  333.671741] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192u'
[  333.673040] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192u; check system log for messages from 'loadndisdriver'
[  333.673157] usbcore: registered new interface driver ndiswrapper
[  371.492076] usb 1-1: USB disconnect, address 3
[  404.570056] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  404.731036] usb 1-1: configuration #1 chosen from 1 choice
[ 1020.255275] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1700.206284] usb 1-1: USB disconnect, address 4
[ 1710.121194] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1710.278891] usb 1-1: configuration #1 chosen from 1 choice
[ 1788.445216] usb 1-1: USB disconnect, address 5
[ 1891.202569] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 1891.360911] usb 1-2: configuration #1 chosen from 1 choice
[ 1891.500086] usb 1-2: reset high speed USB device using ehci_hcd and address 6
[ 1891.663133] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[ 1891.667554] ndiswrapper: driver net8192u (Realtek Semiconductor Corp.,08/14/2008,5.1033.0814.2008) loaded
[ 1891.673541] BUG: unable to handle kernel NULL pointer dereference at 000000000000001c
[ 1891.673557] IP: [<ffffffffa0be32cb>] USBD_InterfaceIsDeviceHighSpeed+0xb/0x20 [ndiswrapper]
[ 1891.673641] PGD 775a9067 PUD 76597067 PMD 0 
[ 1891.673653] Oops: 0000 [#1] SMP 
[ 1891.673661] last sysfs file: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/bInterfaceProtocol
[ 1891.673670] CPU 1 
[ 1891.673675] Modules linked in: ndiswrapper ppdev bridge stp bnep snd_hda_codec_conexant joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq sdhci_pci iptable_filter snd_timer sdhci amd64_edac_mod psmouse lp ip_tables serio_raw snd_seq_device led_class btusb ricoh_mmc edac_core x_tables parport snd i2c_nforce2 k8temp nvidia(P) soundcore snd_page_alloc ohci1394 ieee1394 video output forcedeth
[ 1891.673768] Pid: 26, comm: khubd Tainted: P           2.6.31-14-generic #48-Ubuntu Presario V6000 (EX993AV#ABA)      
[ 1891.673777] RIP: 0010:[<ffffffffa0be32cb>]  [<ffffffffa0be32cb>] USBD_InterfaceIsDeviceHighSpeed+0xb/0x20 [ndiswrapper]
[ 1891.673825] RSP: 0018:ffff8800790b7418  EFLAGS: 00010246
[ 1891.673832] RAX: 0000000000000000 RBX: ffffc900019cf000 RCX: ffff880055073c00
[ 1891.673838] RDX: ffffffffffffffff RSI: 0000000000000000 RDI: ffffc900019cf000
[ 1891.673845] RBP: ffff8800790b7418 R08: 0000000000000000 R09: ffff880044ce6400
[ 1891.673851] R10: ffffffffa0bd58d0 R11: 0000000000000000 R12: ffff880044ce6400
[ 1891.673858] R13: ffff8800790b7528 R14: 0000000000000000 R15: 0000000000000000
[ 1891.673866] FS:  00007fb3de1c1910(0000) GS:ffff880001a12000(0000) knlGS:00000000f69e2750
[ 1891.673874] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[ 1891.673880] CR2: 000000000000001c CR3: 0000000037869000 CR4: 00000000000006e0
[ 1891.673886] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1891.673893] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1891.673901] Process khubd (pid: 26, threadinfo ffff8800790b6000, task ffff8800790b96b0)
[ 1891.673906] Stack:
[ 1891.673910]  0000000000000000 ffffc9000193c604 0000000000000000 ffffc900019cf000
[ 1891.673920] <0> 0000000000000000 ffffc900019cf000 0000000000000012 ffff88007544b580
[ 1891.673931] <0> 0000000100000000 ffff8800790b7460 ffff8800790b7460 ffff8800790b7480
[ 1891.673943] Call Trace:
[ 1891.673985]  [<ffffffffa0bd486b>] ? ExFreePool+0xb/0x10 [ndiswrapper]
[ 1891.674027]  [<ffffffffa0be3440>] ? USBD_InterfaceReference+0x0/0x20 [ndiswrapper]
[ 1891.674070]  [<ffffffffa0be3420>] ? USBD_InterfaceDereference+0x0/0x20 [ndiswrapper]
[ 1891.674112]  [<ffffffffa0be3280>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
[ 1891.674155]  [<ffffffffa0be3950>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
[ 1891.674198]  [<ffffffffa0be33f0>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
[ 1891.674240]  [<ffffffffa0be33c0>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
[ 1891.674283]  [<ffffffffa0be32c0>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
[ 1891.674327]  [<ffffffffa0be103a>] ? mp_init+0x6a/0x200 [ndiswrapper]
[ 1891.674368]  [<ffffffffa0bd90d9>] ? IofCompleteRequest+0x59/0x1c0 [ndiswrapper]
[ 1891.674410]  [<ffffffffa0bdb56d>] ? pdoDispatchPnp+0x3d/0xf0 [ndiswrapper]
[ 1891.674452]  [<ffffffffa0be2117>] ? ndis_start_device+0x27/0x860 [ndiswrapper]
[ 1891.674492]  [<ffffffffa0bd8705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
[ 1891.674509]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
[ 1891.674550]  [<ffffffffa0bd8690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
[ 1891.674591]  [<ffffffffa0bd86d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
[ 1891.674632]  [<ffffffffa0bd8c61>] ? IoSyncForwardIrp+0x91/0xd0 [ndiswrapper]
[ 1891.674674]  [<ffffffffa0be29f3>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[ 1891.674717]  [<ffffffffa0be4ec7>] ? win2lin2+0xe/0x11 [ndiswrapper]
[ 1891.674757]  [<ffffffffa0bd8690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
[ 1891.674797]  [<ffffffffa0bd8705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
[ 1891.674809]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
[ 1891.674849]  [<ffffffffa0bd8690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
[ 1891.674889]  [<ffffffffa0bd86d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
[ 1891.674930]  [<ffffffffa0bda638>] ? IoSendIrpTopDev+0xd8/0x120 [ndiswrapper]
[ 1891.674941]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
[ 1891.674983]  [<ffffffffa0bd8543>] ? IoAttachDeviceToDeviceStack+0x63/0x80 [ndiswrapper]
[ 1891.675024]  [<ffffffffa0bda9f7>] ? pnp_start_device+0x47/0x90 [ndiswrapper]
[ 1891.675066]  [<ffffffffa0bdacf1>] ? wrap_pnp_start_device+0x121/0x180 [ndiswrapper]
[ 1891.675108]  [<ffffffffa0bdae34>] ? wrap_pnp_start_usb_device+0xe4/0x110 [ndiswrapper]
[ 1891.675119]  [<ffffffff81527ef9>] ? mutex_lock+0x19/0x50
[ 1891.675133]  [<ffffffff813a25ed>] ? usb_autopm_do_device+0x7d/0x120
[ 1891.675144]  [<ffffffff813a2e71>] ? usb_probe_interface+0xb1/0x190
[ 1891.675155]  [<ffffffff81320f40>] ? __device_attach+0x0/0x50
[ 1891.675163]  [<ffffffff81320d74>] ? really_probe+0x64/0x160
[ 1891.675171]  [<ffffffff81320f40>] ? __device_attach+0x0/0x50
[ 1891.675179]  [<ffffffff81320f40>] ? __device_attach+0x0/0x50
[ 1891.675188]  [<ffffffff81320e93>] ? driver_probe_device+0x23/0x30
[ 1891.675196]  [<ffffffff81320f8b>] ? __device_attach+0x4b/0x50
[ 1891.675207]  [<ffffffff8131fef8>] ? bus_for_each_drv+0x68/0x90
[ 1891.675216]  [<ffffffff81321046>] ? device_attach+0x86/0x90
[ 1891.675226]  [<ffffffff8131fcf5>] ? bus_probe_device+0x25/0x40
[ 1891.675236]  [<ffffffff8131e6a9>] ? device_add+0x2e9/0x3d0
[ 1891.675247]  [<ffffffff813a1308>] ? usb_set_configuration+0x478/0x780
[ 1891.675256]  [<ffffffff81320f40>] ? __device_attach+0x0/0x50
[ 1891.675266]  [<ffffffff813aabf2>] ? generic_probe+0x32/0xb0
[ 1891.675276]  [<ffffffff81320c5a>] ? driver_sysfs_add+0x5a/0x90
[ 1891.675286]  [<ffffffff813a16e5>] ? usb_probe_device+0x25/0x30
[ 1891.675294]  [<ffffffff81320d74>] ? really_probe+0x64/0x160
[ 1891.675302]  [<ffffffff81320f40>] ? __device_attach+0x0/0x50
[ 1891.675311]  [<ffffffff81320e93>] ? driver_probe_device+0x23/0x30
[ 1891.675319]  [<ffffffff81320f8b>] ? __device_attach+0x4b/0x50
[ 1891.675329]  [<ffffffff8131fef8>] ? bus_for_each_drv+0x68/0x90
[ 1891.675337]  [<ffffffff81321046>] ? device_attach+0x86/0x90
[ 1891.675347]  [<ffffffff8131fcf5>] ? bus_probe_device+0x25/0x40
[ 1891.675357]  [<ffffffff8131e6a9>] ? device_add+0x2e9/0x3d0
[ 1891.675367]  [<ffffffff8139919d>] ? usb_new_device+0x6d/0xe0
[ 1891.675376]  [<ffffffff81399b28>] ? hub_port_connect_change+0x4a8/0x960
[ 1891.675386]  [<ffffffff8139b472>] ? hub_events+0x3a2/0x590
[ 1891.675396]  [<ffffffff815270f9>] ? thread_return+0x48/0x37f
[ 1891.675405]  [<ffffffff8139b660>] ? hub_thread+0x0/0x190
[ 1891.675414]  [<ffffffff8139b69a>] ? hub_thread+0x3a/0x190
[ 1891.675426]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
[ 1891.675435]  [<ffffffff8139b660>] ? hub_thread+0x0/0x190
[ 1891.675444]  [<ffffffff81078746>] ? kthread+0xa6/0xb0
[ 1891.675455]  [<ffffffff810130ea>] ? child_rip+0xa/0x20
[ 1891.675464]  [<ffffffff810786a0>] ? kthread+0x0/0xb0
[ 1891.675472]  [<ffffffff810130e0>] ? child_rip+0x0/0x20
[ 1891.675477] Code: 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 c9 c3 66 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 48 8b 87 98 00 00 00 55 48 89 e5 <83> 78 1c 03 c9 0f 94 c0 c3 66 66 66 2e 0f 1f 84 00 00 00 00 00 
[ 1891.675567] RIP  [<ffffffffa0be32cb>] USBD_InterfaceIsDeviceHighSpeed+0xb/0x20 [ndiswrapper]
[ 1891.675614]  RSP <ffff8800790b7418>
[ 1891.675618] CR2: 000000000000001c
[ 1891.675630] ---[ end trace a3c8455e91d5757e ]---

```I am running an AMD64 system. I have tried both the WinXP64 and WinXP2K (32 bit drivers). The 32 bit driver fails with the 'bad:magic' message in the dmesg output. I have also attempted building ndiswrapper from source, with the same results.

If anyone has any suggestions as to what else I should try let me know.

Thanks,
John

---

### Post by aDragonfly on 2009-11-21
I've got the same problem with a Realtek USB 8192 nic.  It works fine if I run a 32 bit linux (live session) and load the 32 bit drivers, but hangs on 64 bit with 64 bit drivers.  It appears to completely hang the USB interface (and occasionally the whole system).

Anyone have any ideas?

---

### Post by WakkiTabakki on 2010-04-14
Hi all
I have the same problem:
- Lucid 64bit (kernel 2.6.31-19)
- D-Link DWA-131 USB 

The Linux drivers provided by D-Link does not compile.

The drivers from RealTek (r8192su) compiles with a pile of warning about incompatible int-sizes without casts. But completely freezes the computer when dongle is connected.

Ndiswrapper with the 64bit driver gives me the "null pointer deference" error and also kills the USB-subsystem.

Did anyone find a solution?
/N

---

