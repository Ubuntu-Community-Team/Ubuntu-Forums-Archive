---
title: "iwl3945 taking high system load"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by jwwadk on 2009-01-22
Hello all,
I have been using Intrepid Ibex for about a month now (having come from Hardy), and I have been noticing a problem with iwl3945, namely that at seemingly random intervals it will take very large chunks of my system load, and will cause a momentary lockup. Needless to say, this is very annoying. Below is the result of dmesg | grep -i iwl :

[   13.702343] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.702346] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.703670] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.703678] iwlagn 0000:07:00.0: setting latency timer to 64
[   13.703698] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.747729] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.802958] iwlagn 0000:07:00.0: PCI INT A disabled
[   13.803262] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   29.850881] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.850947] iwlagn 0000:07:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   29.851071] firmware: requesting iwlwifi-4965-2.ucode
[   30.837542] Registered led device: iwl-phy0:radio
[   30.837574] Registered led device: iwl-phy0:assoc
[   30.837587] Registered led device: iwl-phy0:RX
[   30.837600] Registered led device: iwl-phy0:TX
[  441.188452] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[  443.397145] Registered led device: iwl-phy0:radio
[  443.398051] Registered led device: iwl-phy0:assoc
[  443.398177] Registered led device: iwl-phy0:RX
[  443.398294] Registered led device: iwl-phy0:TX
[  579.000382] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[  579.025613] iwlagn: MAC is in deep sleep!
[  579.225572] Registered led device: iwl-phy0:radio
[  579.225625] Registered led device: iwl-phy0:assoc
[  579.225663] Registered led device: iwl-phy0:RX
[  579.225699] Registered led device: iwl-phy0:TX
[  583.010601] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[  583.036400] iwlagn: MAC is in deep sleep!
[  583.250045] Registered led device: iwl-phy0:radio
[  583.250095] Registered led device: iwl-phy0:assoc
[  583.250139] Registered led device: iwl-phy0:RX
[  583.250176] Registered led device: iwl-phy0:TX
[  587.175965] iwlagn: Microcode SW error detected.  Restarting 0x2000000.

This cycle of "Microcode SW" errors goes on and seems to become more frequent as the computer is left on longer. The only solution that I have found is to use the kill switch on my laptop's wireless card. This seems to restore normal operation. 

My laptop is an Asus M50sv-A1 with a hardware kill switch. 
Any and all assistance is appreciated. 

Thanks.

---

### Post by salubrium on 2009-07-27
When you say very large chunks of system load, how bad is it? I just waited for 20 minutes to be able to get a terminal and kill a rogue Java process (Eclipse) that was chewing IO but when I checked messages log, what I saw seems similar to your issue, which I have added my report here but none of them report high load.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343323)

Here's my: dmesg | grep -i iwl

[221517.505253] iwlagn 0000:0c:00.0: enabling device (0000 -> 0002)
[221517.505327] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[221517.505399] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf9ffe004)
[221517.505420] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)      
[221517.505441] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100506)
[221523.896539] Modules linked in: isofs udf crc_itu_t wacom cbc aes_x86_64 aes_generic binfmt_misc ppdev bnep vboxnetadp vboxnetflt vboxdrv ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp kvm_intel kvm input_polldev joydev lp parport arc4 ecb uvcvideo iwlagn compat_ioctl32 iwlcore psmouse video dcdbas videodev lbm_cw_mac80211 led_class v4l1_compat sdhci_pci sdhci serio_raw iTCO_wdt iTCO_vendor_support pcspkr snd_hda_intel output snd_pcm_oss snd_mixer_oss intel_agp snd_pcm btusb usbhid snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc nvidia(P) lbm_cw_cfg80211 b44 ssb ohci1394 pcmcia pcmcia_core mii ieee1394 vesafb fbcon tileblit font bitblit softcursor                                                                                                                                         
[221530.926396] Registered led device: iwl-phy0::radio                                                                                       
[221530.926433] Registered led device: iwl-phy0::assoc                                                                                       
[221530.926450] Registered led device: iwl-phy0::RX                                                                                          
[221530.926467] Registered led device: iwl-phy0::TX                                                                                          
[221530.999123] iwlagn 0000:0c:00.0: TX Power requested while scanning!                                                                      
[274568.097257] iwlagn 0000:0c:00.0: enabling device (0000 -> 0002)                                                                          
[274568.097332] iwlagn 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)                                         
[274568.097403] iwlagn 0000:0c:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf9ffe004)                                      
[274568.097418] iwlagn 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)                                            
[274568.097434] iwlagn 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100506)                                   
[274574.014633] Modules linked in: isofs udf crc_itu_t wacom cbc aes_x86_64 aes_generic binfmt_misc ppdev bnep vboxnetadp vboxnetflt vboxdrv ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables bridge stp kvm_intel kvm input_polldev joydev lp parport arc4 ecb uvcvideo iwlagn compat_ioctl32 iwlcore psmouse video dcdbas videodev lbm_cw_mac80211 led_class v4l1_compat sdhci_pci sdhci serio_raw iTCO_wdt iTCO_vendor_support pcspkr snd_hda_intel output snd_pcm_oss snd_mixer_oss intel_agp snd_pcm btusb usbhid snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc nvidia(P) lbm_cw_cfg80211 b44 ssb ohci1394 pcmcia pcmcia_core mii ieee1394 vesafb fbcon tileblit font bitblit softcursor                                                                                                                                         
[274582.729324] Registered led device: iwl-phy0::radio                                                                                       
[274582.729353] Registered led device: iwl-phy0::assoc                                                                                       
[274582.729370] Registered led device: iwl-phy0::RX                                                                                          
[274582.729385] Registered led device: iwl-phy0::TX                                                                                          
[286480.761066] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x2000000.                                                     
[286487.785165] iwlagn 0000:0c:00.0: index 0 not used in uCode key table.
[286487.785177] iwlagn 0000:0c:00.0: No space for Tx
[286487.785183] iwlagn 0000:0c:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -28
[286487.785645] iwlagn 0000:0c:00.0: No space for Tx
[286487.785651] iwlagn 0000:0c:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[286487.785657] iwlagn 0000:0c:00.0: SENSITIVITY_CMD failed
[286487.996684] Registered led device: iwl-phy0::radio
[286487.996723] Registered led device: iwl-phy0::assoc
[286487.996760] Registered led device: iwl-phy0::RX
[286487.996795] Registered led device: iwl-phy0::TX
[286503.692253] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x2000000.
[286548.946202] Registered led device: iwl-phy0::radio
[286548.946241] Registered led device: iwl-phy0::assoc
[286548.946275] Registered led device: iwl-phy0::RX
[286548.946309] Registered led device: iwl-phy0::TX
[286609.140174] iwlagn 0000:0c:00.0: Microcode SW error detected.  Restarting 0x2000000.
[286618.614028] Registered led device: iwl-phy0::radio
[286618.614055] Registered led device: iwl-phy0::assoc
[286618.614079] Registered led device: iwl-phy0::RX
[286618.614103] Registered led device: iwl-phy0::TX
[287354.090730]  [<ffffffffa0aa44c0>] iwl_tx_queue_init+0xe0/0x310 [iwlcore]
[287354.090772]  [<ffffffffa0aa6031>] iwl_txq_ctx_reset+0x2f1/0x600 [iwlcore]
[287354.090796]  [<ffffffffa0aa28d5>] ? iwl_rx_queue_update_write_ptr+0x55/0x1e0 [iwlcore]
[287354.090820]  [<ffffffffa0a9e92b>] iwl_hw_nic_init+0xfb/0x180 [iwlcore]
[287354.090838]  [<ffffffffa0ac9f20>] __iwl_up+0xb0/0x360 [iwlagn]
[287354.090853]  [<ffffffffa0aca8b8>] iwl_mac_start+0x568/0x970 [iwlagn]
[287354.113080] iwlagn 0000:0c:00.0: kmalloc for auxiliary BD structures failed
[287354.113177] iwlagn 0000:0c:00.0: Tx 10 queue init failed
[287354.114038] iwlagn 0000:0c:00.0: Unable to init nic

---

