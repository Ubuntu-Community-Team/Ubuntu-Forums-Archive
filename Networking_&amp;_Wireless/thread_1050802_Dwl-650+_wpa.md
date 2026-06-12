---
title: "Dwl-650+ wpa"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Vermind on 2009-01-26
Hi,
I have a DWL-650+ wireless PCMCIA adapter, supported by the acx driver. However, when the system boots and loads the driver, I see a stacktrace in dmesg, and it does not work.

On the other hand, the TIACX or AIRPLUS Windows drivers via ndiswrapper do not support WPA, and the rest of my network uses WPA. The same drivers (AIRPLUS) work in Windows for WPA, but in Ubuntu, NetworkManager does not let me type in a WPA key, the choices are WEP, ..., LEAP. However, adding a key manually by "edit wireless networks" works; but the connectivity is like 2 secs connected, 5 secs disconnected, reconnecting...

So, I am asking how to get WPA working on DWL-650+ (the ACX 100 22M Texas Instruments model)

Oh, and in dmesg, ndiswrapper says that WPA with TKIP IS supported by the drivers.

Dmesg for acx:
```
[  285.705904] acx_pci 0000:03:00.0: enabling device (0000 -> 0003)
[  285.705919] acx_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  285.705928] acx_pci 0000:03:00.0: setting latency timer to 64
[  285.705955] acx: found ACX100-based wireless network card at 0000:03:00.0, irq:17, phymem1:0x58010000, phymem2:0x58000000, mem1:0xf8abe000, mem1_size:4096, mem2:0xf8b80000, mem2_size:65536
[  285.707946] acx: loading firmware for acx100 chipset with radio ID 0D
[  285.707954] firmware: requesting acx/default/tiacx100c0D
[  285.716759] acx: firmware image 'acx/default/tiacx100c0D' was not provided. Check your hotplug scripts
[  285.716768] firmware: requesting acx/default/tiacx100
[  286.008125] acx: loading radio image for radio 0D
[  286.020041] firmware: requesting acx/default/tiacx100r0D
[  286.448426] NVS_vendor_offs:0000 probe_delay:500 eof_memory:65536
[  286.448434] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[  286.448437] AntennaID:00 Len:02 Data:01 02 
[  286.448440] PowerLevelID:01 Len:02 Data:001E 000A 
[  286.448444] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[  286.448449] DomainID:03 Len:06 Data:30 20 10 31 32 41 
[  286.448455] ProductID:04 Len:09 Data:TI ACX100
[  286.448457] ManufacturerID:05 Len:07 Data:TI Test
[  286.532024] acx: === chipset TNETW1100B, radio type 0x0D (Maxim), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.9.8.b' ===
[  286.536595] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-11-generic
[  290.600015] wlan0: changing radio power level to 18 dBm (23)
[  309.328016] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:0 (Idle)
[  309.328025] wlan0: issue_cmd(cmd:0x0016) FAILED
[  309.328030] Pid: 4979, comm: wpa_supplicant Tainted: P        W 2.6.27-11-generic #1
[  309.328035]  [<c037d236>] ? printk+0x1d/0x1f
[  309.328048]  [<f8ba5749>] acxpci_s_issue_cmd_timeo+0x269/0x3b0 [acx]
[  309.328077]  [<f8ba0a8a>] acx_s_set_probe_request_template+0x14a/0x160 [acx]
[  309.328087]  [<f8ba18c3>] acx_s_update_card_settings+0xca3/0x1110 [acx]
[  309.328096]  [<c012a778>] ? enqueue_task_fair+0x48/0x50
[  309.328104]  [<c012b55e>] ? try_to_wake_up+0xde/0x290
[  309.328108]  [<c030f8bd>] ? __nla_put+0x1d/0x50
[  309.328114]  [<c036a22f>] ? wireless_send_event+0x15f/0x230
[  309.328120]  [<c036a22f>] ? wireless_send_event+0x15f/0x230
[  309.328124]  [<c014c1a0>] ? up+0x30/0x50
[  309.328129]  [<c036aa97>] ? ioctl_standard_iw_point+0x127/0x290
[  309.328134]  [<c036aa97>] ? ioctl_standard_iw_point+0x127/0x290
[  309.328139]  [<f8b9bfd6>] acx_ioctl_commit+0x26/0x40 [acx]
[  309.328148]  [<f8b9bfb0>] ? acx_ioctl_commit+0x0/0x40 [acx]
[  309.328157]  [<c036acbc>] ioctl_standard_call+0xbc/0x110
[  309.328161]  [<c02f3115>] ? __dev_get_by_name+0x85/0xb0
[  309.328168]  [<c036a52e>] wireless_process_ioctl+0xbe/0x150
[  309.328172]  [<f8b9ba50>] ? acx_ioctl_set_encode+0x0/0x1a0 [acx]
[  309.328179]  [<c037e260>] ? mutex_lock+0x10/0x20
[  309.328184]  [<c036a630>] wext_handle_ioctl+0x70/0xe0
[  309.328188]  [<c036ac00>] ? ioctl_standard_call+0x0/0x110
[  309.328192]  [<c036a7f0>] ? ioctl_private_call+0x0/0x180
[  309.328196]  [<c02f526f>] dev_ioctl+0x45f/0x520
[  309.328199]  [<c01955a0>] ? unmap_vmas+0x1a0/0x360
[  309.328204]  [<c037f45d>] ? _spin_lock+0xd/0x10
[  309.328209]  [<c0199524>] ? unlink_file_vma+0x14/0xa0
[  309.328213]  [<c02e57e0>] ? sock_ioctl+0x0/0x250
[  309.328217]  [<c02e58d5>] sock_ioctl+0xf5/0x250
[  309.328223]  [<c02e57e0>] ? sock_ioctl+0x0/0x250
[  309.328226]  [<c01bf16d>] vfs_ioctl+0x2d/0x90
[  309.328231]  [<c01bf356>] do_vfs_ioctl+0x66/0x200
[  309.328235]  [<c0214df8>] ? cap_file_ioctl+0x8/0x10
[  309.328241]  [<c01bf55b>] sys_ioctl+0x6b/0x70
[  309.328244]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[  309.328250]  =======================
```

Dmesg for ndiswrapper:
```
[  326.784029] pccard: CardBus card inserted into slot 0
[  326.784074] PCI: 0000:03:00.0 reg 10 io port: [0, 1f]
[  326.784084] PCI: 0000:03:00.0 reg 14 32bit mmio: [0, fff]
[  326.784092] PCI: 0000:03:00.0 reg 18 32bit mmio: [0, ffff]
[  326.784136] pci 0000:03:00.0: supports D1
[  326.784138] pci 0000:03:00.0: supports D2
[  326.784141] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[  326.784147] pci 0000:03:00.0: PME# disabled
[  326.897407] ndiswrapper: driver tiacxln (,06/05/2004,4.15.8.2) loaded
[  326.898691] ndiswrapper 0000:03:00.0: enabling device (0000 -> 0003)
[  326.898703] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  326.898908] ndiswrapper 0000:03:00.0: setting latency timer to 64
[  326.899423] ndiswrapper: using IRQ 17
[  327.504577] wlan0: ethernet device 00:0f:3d:46:61:05 using NDIS driver: tiacxln, version: 0x4000f, NDIS version: 0x501, vendor: '22M WLAN Adapter', 104C:8400.5.conf
[  327.505691] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
[  327.505978] wlan0: encryption modes supported: WEP; TKIP with WPA
... (unrelated messages)
[  537.587706] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)
```

---

### Post by Zenguy on 2009-12-22
I'm pretty sure that the DWL-650+ does not support WPA.

---

### Post by TaperChuck on 2010-03-10
My first post here...

I'm a total ubuntu/linux newbie...
I just installed ubuntu on my Gateway Solo 2150. Hoping it will be faster and better to web browse than Windows 2000. :D

I also have the DWL-650+ PCMCIA wireless adapter.
My problem is... the computer doesn't recognize it. It doesn't light up and the computer doesn't seem to know that it's there.

Can someone point me to instructions or explain *exactly* what I have to do to make the system recognize and use the DWL-650+ PCMCIA wireless adapter? I did find a linux driver for it. I just don't know how to install it correctly.

Thanks in advance,
Chuck

---

