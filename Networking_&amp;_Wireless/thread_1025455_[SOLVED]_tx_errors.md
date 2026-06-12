---
title: "[SOLVED] tx errors"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by nzadLithium on 2008-12-30
My network connection goes fine for a while, then it decides to throw up these errors and it lags like mad till it eventually loses connection. Basically dmesg fills up with stuff like this:

```
[ 7594.738789] wlan0: tx error 0x20, buf 10!
[ 7660.752754] wlan0: tx error 0x20, buf 02!
[ 7662.449687] wlan0: tx error 0x20, buf 03!
[ 7662.467451] wlan0: tx error 0x20, buf 04!
[ 7662.487566] wlan0: tx error 0x20, buf 05!
[ 7662.514370] wlan0: tx error 0x20, buf 06!
[ 7662.578021] wlan0: tx error 0x20, buf 07!
[ 7662.870788] wlan0: tx error 0x20, buf 08!
[ 7669.234869] wlan0: tx error 0x20, buf 02!
[ 7670.527272] wlan0: tx error 0x20, buf 03!
[ 7670.783363] wlan0: tx error 0x20, buf 04!
[ 7670.896885] wlan0: tx error 0x20, buf 05!
[ 7673.658313] wlan0: tx error 0x20, buf 07!
[ 7675.275137] wlan0: tx error 0x20, buf 08!
[ 7677.633599] wlan0: tx error 0x20, buf 10!
[ 7678.702606] wlan0: tx error 0x20, buf 11!
[ 7678.825861] wlan0: tx error 0x20, buf 12!
[ 7680.616667] wlan0: tx error 0x20, buf 13!
```

lspci of network card
05:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

I also get stuff like this sometimes as well
```
[ 7570.813481] wlan0: several excessive Tx retry errors occurred, attempting to recalibrate radio. Radio drift might be caused by increasing card temperature, please check the card before it's too late!
[ 7570.813484] disabling above message
[ 7570.813489] wlan0: tx error 0x20, buf 08!
[ 7570.813554] wlan0: less than 5 minutes since last radio recalibration, no
```

loading of module
```
[ 7952.688074] usbcore: deregistering interface driver acx_usb
[ 7956.839855] acx: Loaded combined PCI/USB driver, firmware_ver=default
[ 7956.839867] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[ 7956.860065] acx_pci 0000:05:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[ 7956.860109] acx: found ACX111-based wireless network card at 0000:05:08.0, irq:18, phymem1:0xC3024000, phymem2:0xC3000000, mem1:0xffffc20000334000, mem1_size:8192, mem2:0xffffc20000340000, mem2_size:131072
[ 7956.867696] acx: loading firmware for acx1111 chipset with radio ID 16
[ 7956.867709] firmware: requesting acx/1.2.1.34/tiacx111c16
[ 7957.504499] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[ 7957.504511] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[ 7957.504515] AntennaID:00 Len:02 Data:01 02 
[ 7957.504520] PowerLevelID:01 Len:02 Data:001E 000A 
[ 7957.504525] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[ 7957.504531] DomainID:03 Len:06 Data:41 20 30 31 32 40 
[ 7957.504539] ProductID:04 Len:09 Data:TI ACX100
[ 7957.504542] ManufacturerID:05 Len:07 Data:TI Test
[ 7957.564032] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[ 7957.572223] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-9-generic
[ 7957.573025] usbcore: registered new interface driver acx_usb

```

and on removing acx module i get:
```
[ 8036.508044] ------------[ cut here ]------------
[ 8036.508055] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/pci-dma.c:376 dma_free_coherent+0xba/0xc0()
[ 8036.508060] Modules linked in: acx(-) ipt_REJECT xt_limit xt_state af_packet tuner_simple tuner_types tea5767 tuner tvaudio bttv ir_common compat_ioctl32 videodev v4l1_compat i2c_algo_bit v4l2_common videobuf_dma_sg videobuf_core btcx_risc tveeprom binfmt_misc b44 ssb mii ndiswrapper nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs ipx p8023 ipv6 powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative wmi video output sbs sbshc pci_slot container battery ipt_LOG iptable_filter nls_iso8859_1 nls_cp437 vfat fat ac it87 hwmon_vid lp nvidia(P) snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy psmouse serio_raw snd_seq_oss pcspkr k8temp snd_seq_midi shpchp pci_hotplug snd_rawmidi snd_seq_midi_event snd_seq emu10k1_gp snd_timer snd_seq_device gameport snd soundcore joydev evdev parport_pc parport i2c_nforce2 i2c_core button ipt_MASQUERADE xt_mark xt_tcpudp xt_MARK iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack ip_tables x_tables ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid pata_amd sata_nv pata_acpi forcedeth ohci1394 ata_generic ieee1394 libata ehci_hcd ohci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: acx]
[ 8036.508207] Pid: 15722, comm: rmmod Tainted: P        W 2.6.27-9-generic #1
[ 8036.508210] 
[ 8036.508211] Call Trace:
[ 8036.508221]  [<ffffffff8024e9b4>] warn_on_slowpath+0x64/0x90
[ 8036.508229]  [<ffffffff80502504>] ? _spin_lock_irqsave+0x34/0x50
[ 8036.508235]  [<ffffffff8025a84b>] ? lock_timer_base+0x3b/0x70
[ 8036.508240]  [<ffffffff8025a8df>] ? try_to_del_timer_sync+0x5f/0x70
[ 8036.508245]  [<ffffffff8025a912>] ? del_timer_sync+0x22/0x30
[ 8036.508250]  [<ffffffff80500e2b>] ? schedule_timeout+0x6b/0xd0
[ 8036.508256]  [<ffffffff8021820a>] dma_free_coherent+0xba/0xc0
[ 8036.508273]  [<ffffffffa02d3e51>] acxpci_free_desc_queues+0x31/0x110 [acx]
[ 8036.508285]  [<ffffffffa02d3f84>] acxpci_s_delete_dma_regions+0x54/0x70 [acx]
[ 8036.508297]  [<ffffffffa02d74c3>] acxpci_e_remove+0x123/0x30d [acx]
[ 8036.508312]  [<ffffffff803bbfb4>] pci_device_remove+0x34/0x70
[ 8036.508319]  [<ffffffff80430212>] __device_release_driver+0xa2/0xe0
[ 8036.508327]  [<ffffffff80430328>] driver_detach+0xd8/0xe0
[ 8036.508336]  [<ffffffff8042f2c6>] bus_remove_driver+0x96/0xd0
[ 8036.508344]  [<ffffffff80278fe0>] ? __try_stop_module+0x0/0x50
[ 8036.508355]  [<ffffffff804308b7>] driver_unregister+0x47/0x50
[ 8036.508365]  [<ffffffff803bc31c>] pci_unregister_driver+0x3c/0xb0
[ 8036.508378]  [<ffffffffa02d6bee>] acxpci_e_cleanup_module+0x15/0x17 [acx]
[ 8036.508390]  [<ffffffffa02d6bd2>] acx_e_cleanup_module+0xe/0x15 [acx]
[ 8036.508395]  [<ffffffff8027b9a7>] sys_delete_module+0x1c7/0x2a0
[ 8036.508402]  [<ffffffff803a7c78>] ? __up_write+0x68/0x140
[ 8036.508413]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[ 8036.508416] 
[ 8036.508419] ---[ end trace 055485033ce42cd1 ]---
[ 8036.508424] ------------[ cut here ]------------
[ 8036.508428] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/pci-dma.c:376 dma_free_coherent+0xba/0xc0()
[ 8036.508432] Modules linked in: acx(-) ipt_REJECT xt_limit xt_state af_packet tuner_simple tuner_types tea5767 tuner tvaudio bttv ir_common compat_ioctl32 videodev v4l1_compat i2c_algo_bit v4l2_common videobuf_dma_sg videobuf_core btcx_risc tveeprom binfmt_misc b44 ssb mii ndiswrapper nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs ipx p8023 ipv6 powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative wmi video output sbs sbshc pci_slot container battery ipt_LOG iptable_filter nls_iso8859_1 nls_cp437 vfat fat ac it87 hwmon_vid lp nvidia(P) snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy psmouse serio_raw snd_seq_oss pcspkr k8temp snd_seq_midi shpchp pci_hotplug snd_rawmidi snd_seq_midi_event snd_seq emu10k1_gp snd_timer snd_seq_device gameport snd soundcore joydev evdev parport_pc parport i2c_nforce2 i2c_core button ipt_MASQUERADE xt_mark xt_tcpudp xt_MARK iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack ip_tables x_tables ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid pata_amd sata_nv pata_acpi forcedeth ohci1394 ata_generic ieee1394 libata ehci_hcd ohci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: acx]
[ 8036.508559] Pid: 15722, comm: rmmod Tainted: P        W 2.6.27-9-generic #1
[ 8036.508562] 
[ 8036.508563] Call Trace:
[ 8036.508568]  [<ffffffff8024e9b4>] warn_on_slowpath+0x64/0x90
[ 8036.508574]  [<ffffffff80502504>] ? _spin_lock_irqsave+0x34/0x50
[ 8036.508579]  [<ffffffff8025a84b>] ? lock_timer_base+0x3b/0x70
[ 8036.508586]  [<ffffffff802b1539>] ? get_pageblock_flags_group+0x9/0xa0
[ 8036.508592]  [<ffffffff802b3460>] ? free_hot_page+0x10/0x20
[ 8036.508598]  [<ffffffff802b3e15>] ? __free_pages+0x35/0x40
[ 8036.508603]  [<ffffffff8021820a>] dma_free_coherent+0xba/0xc0
[ 8036.508615]  [<ffffffffa02d3e86>] acxpci_free_desc_queues+0x66/0x110 [acx]
[ 8036.508627]  [<ffffffffa02d3f84>] acxpci_s_delete_dma_regions+0x54/0x70 [acx]
[ 8036.508638]  [<ffffffffa02d74c3>] acxpci_e_remove+0x123/0x30d [acx]
[ 8036.508651]  [<ffffffff803bbfb4>] pci_device_remove+0x34/0x70
[ 8036.508657]  [<ffffffff80430212>] __device_release_driver+0xa2/0xe0
[ 8036.508665]  [<ffffffff80430328>] driver_detach+0xd8/0xe0
[ 8036.508674]  [<ffffffff8042f2c6>] bus_remove_driver+0x96/0xd0
[ 8036.508680]  [<ffffffff80278fe0>] ? __try_stop_module+0x0/0x50
[ 8036.508692]  [<ffffffff804308b7>] driver_unregister+0x47/0x50
[ 8036.508701]  [<ffffffff803bc31c>] pci_unregister_driver+0x3c/0xb0
[ 8036.508715]  [<ffffffffa02d6bee>] acxpci_e_cleanup_module+0x15/0x17 [acx]
[ 8036.508726]  [<ffffffffa02d6bd2>] acx_e_cleanup_module+0xe/0x15 [acx]
[ 8036.508731]  [<ffffffff8027b9a7>] sys_delete_module+0x1c7/0x2a0
[ 8036.508737]  [<ffffffff803a7c78>] ? __up_write+0x68/0x140
[ 8036.508746]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[ 8036.508749] 
[ 8036.508751] ---[ end trace 055485033ce42cd1 ]---
[ 8036.508758] ------------[ cut here ]------------
[ 8036.508761] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/pci-dma.c:376 dma_free_coherent+0xba/0xc0()
[ 8036.508765] Modules linked in: acx(-) ipt_REJECT xt_limit xt_state af_packet tuner_simple tuner_types tea5767 tuner tvaudio bttv ir_common compat_ioctl32 videodev v4l1_compat i2c_algo_bit v4l2_common videobuf_dma_sg videobuf_core btcx_risc tveeprom binfmt_misc b44 ssb mii ndiswrapper nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs ipx p8023 ipv6 powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative wmi video output sbs sbshc pci_slot container battery ipt_LOG iptable_filter nls_iso8859_1 nls_cp437 vfat fat ac it87 hwmon_vid lp nvidia(P) snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy psmouse serio_raw snd_seq_oss pcspkr k8temp snd_seq_midi shpchp pci_hotplug snd_rawmidi snd_seq_midi_event snd_seq emu10k1_gp snd_timer snd_seq_device gameport snd soundcore joydev evdev parport_pc parport i2c_nforce2 i2c_core button ipt_MASQUERADE xt_mark xt_tcpudp xt_MARK iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack ip_tables x_tables ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid pata_amd sata_nv pata_acpi forcedeth ohci1394 ata_generic ieee1394 libata ehci_hcd ohci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: acx]
[ 8036.508892] Pid: 15722, comm: rmmod Tainted: P        W 2.6.27-9-generic #1
[ 8036.508895] 
[ 8036.508896] Call Trace:
[ 8036.508901]  [<ffffffff8024e9b4>] warn_on_slowpath+0x64/0x90
[ 8036.508907]  [<ffffffff80502504>] ? _spin_lock_irqsave+0x34/0x50
[ 8036.508912]  [<ffffffff8025a84b>] ? lock_timer_base+0x3b/0x70
[ 8036.508918]  [<ffffffff802bbc49>] ? __mod_zone_page_state+0x9/0x70
[ 8036.508924]  [<ffffffff802b3dfd>] ? __free_pages+0x1d/0x40
[ 8036.508929]  [<ffffffff8021820a>] dma_free_coherent+0xba/0xc0
[ 8036.508941]  [<ffffffffa02d3ec6>] acxpci_free_desc_queues+0xa6/0x110 [acx]
[ 8036.508953]  [<ffffffffa02d3f84>] acxpci_s_delete_dma_regions+0x54/0x70 [acx]
[ 8036.508964]  [<ffffffffa02d74c3>] acxpci_e_remove+0x123/0x30d [acx]
[ 8036.508977]  [<ffffffff803bbfb4>] pci_device_remove+0x34/0x70
[ 8036.508983]  [<ffffffff80430212>] __device_release_driver+0xa2/0xe0
[ 8036.508991]  [<ffffffff80430328>] driver_detach+0xd8/0xe0
[ 8036.509000]  [<ffffffff8042f2c6>] bus_remove_driver+0x96/0xd0
[ 8036.509006]  [<ffffffff80278fe0>] ? __try_stop_module+0x0/0x50
[ 8036.509018]  [<ffffffff804308b7>] driver_unregister+0x47/0x50
[ 8036.509027]  [<ffffffff803bc31c>] pci_unregister_driver+0x3c/0xb0
[ 8036.509041]  [<ffffffffa02d6bee>] acxpci_e_cleanup_module+0x15/0x17 [acx]
[ 8036.509051]  [<ffffffffa02d6bd2>] acx_e_cleanup_module+0xe/0x15 [acx]
[ 8036.509056]  [<ffffffff8027b9a7>] sys_delete_module+0x1c7/0x2a0
[ 8036.509062]  [<ffffffff803a7c78>] ? __up_write+0x68/0x140
[ 8036.509071]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[ 8036.509075] 
[ 8036.509077] ---[ end trace 055485033ce42cd1 ]---
[ 8036.509082] ------------[ cut here ]------------
[ 8036.509085] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/pci-dma.c:376 dma_free_coherent+0xba/0xc0()
[ 8036.509089] Modules linked in: acx(-) ipt_REJECT xt_limit xt_state af_packet tuner_simple tuner_types tea5767 tuner tvaudio bttv ir_common compat_ioctl32 videodev v4l1_compat i2c_algo_bit v4l2_common videobuf_dma_sg videobuf_core btcx_risc tveeprom binfmt_misc b44 ssb mii ndiswrapper nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs ipx p8023 ipv6 powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative wmi video output sbs sbshc pci_slot container battery ipt_LOG iptable_filter nls_iso8859_1 nls_cp437 vfat fat ac it87 hwmon_vid lp nvidia(P) snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy psmouse serio_raw snd_seq_oss pcspkr k8temp snd_seq_midi shpchp pci_hotplug snd_rawmidi snd_seq_midi_event snd_seq emu10k1_gp snd_timer snd_seq_device gameport snd soundcore joydev evdev parport_pc parport i2c_nforce2 i2c_core button ipt_MASQUERADE xt_mark xt_tcpudp xt_MARK iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack ip_tables x_tables ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid pata_amd sata_nv pata_acpi forcedeth ohci1394 ata_generic ieee1394 libata ehci_hcd ohci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: acx]
[ 8036.509216] Pid: 15722, comm: rmmod Tainted: P        W 2.6.27-9-generic #1
[ 8036.509219] 
[ 8036.509220] Call Trace:
[ 8036.509224]  [<ffffffff8024e9b4>] warn_on_slowpath+0x64/0x90
[ 8036.509230]  [<ffffffff80502504>] ? _spin_lock_irqsave+0x34/0x50
[ 8036.509235]  [<ffffffff8025a84b>] ? lock_timer_base+0x3b/0x70
[ 8036.509241]  [<ffffffff802b1539>] ? get_pageblock_flags_group+0x9/0xa0
[ 8036.509247]  [<ffffffff802b3460>] ? free_hot_page+0x10/0x20
[ 8036.509253]  [<ffffffff802b3e15>] ? __free_pages+0x35/0x40
[ 8036.509258]  [<ffffffff8021820a>] dma_free_coherent+0xba/0xc0
[ 8036.509270]  [<ffffffffa02d3efb>] acxpci_free_desc_queues+0xdb/0x110 [acx]
[ 8036.509281]  [<ffffffffa02d3f84>] acxpci_s_delete_dma_regions+0x54/0x70 [acx]
[ 8036.509293]  [<ffffffffa02d74c3>] acxpci_e_remove+0x123/0x30d [acx]
[ 8036.509305]  [<ffffffff803bbfb4>] pci_device_remove+0x34/0x70
[ 8036.509311]  [<ffffffff80430212>] __device_release_driver+0xa2/0xe0
[ 8036.509319]  [<ffffffff80430328>] driver_detach+0xd8/0xe0
[ 8036.509328]  [<ffffffff8042f2c6>] bus_remove_driver+0x96/0xd0
[ 8036.509335]  [<ffffffff80278fe0>] ? __try_stop_module+0x0/0x50
[ 8036.509346]  [<ffffffff804308b7>] driver_unregister+0x47/0x50
[ 8036.509356]  [<ffffffff803bc31c>] pci_unregister_driver+0x3c/0xb0
[ 8036.509369]  [<ffffffffa02d6bee>] acxpci_e_cleanup_module+0x15/0x17 [acx]
[ 8036.509380]  [<ffffffffa02d6bd2>] acx_e_cleanup_module+0xe/0x15 [acx]
[ 8036.509385]  [<ffffffff8027b9a7>] sys_delete_module+0x1c7/0x2a0
[ 8036.509391]  [<ffffffff803a7c78>] ? __up_write+0x68/0x140
[ 8036.509400]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[ 8036.509403] 
[ 8036.509405] ---[ end trace 055485033ce42cd1 ]---
[ 8036.536188] acx_pci 0000:05:08.0: PCI INT A disabled
[ 8036.552090] usbcore: deregistering interface driver acx_usb

```

I don't understand why this is happening, it started about 2 days ago and has been doing it continuosly ever since, the connection probably lasts about 15 minutes, then does it and its really annoying!!!!!!!!!

Anyone have any ideas how to fix or even whats happening? XD

---

### Post by nzadLithium on 2008-12-30
lol I seem to do this alot, post up on here then find a fix half an hour later. I switched pci slots and cleaned out the truckloads of dust in my case (it told me Radio drift might be caused by increasing card temperature, please check the card before it's too late! so i assumed heat might be building up from dust).

And i haven't lost my connection yet, so i'm hoping all is good XD

---

### Post by Eversmann on 2009-03-14
For the known, same problem, on an UsRobotics card with acx 111 texas instrument chipset, ubuntu 8.10.

Once i switched the card to a different pci slot, everything worked ok.

---

