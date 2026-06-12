---
title: "random wireles network drop."
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by kisain on 2012-12-19
so i have a samsung series 7 700Z5A-S0A, and im getting random disconnects where the card still "seems" to be connected to the router, but nothing is happning, i've managed to locate the error in dmesg but don't know what it means, ill try to include below whatever information i can to help.

ubuntu 12.04 32bit

wireless driver : iwlwifi

wireless card: 02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)

here is the the output from dmesg

[13697.525293] iwlwifi 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[13697.525298] iwlwifi 0000:02:00.0: Loaded firmware version: 18.168.6.1
[13697.525525] iwlwifi 0000:02:00.0: Start IWL Error Log Dump:
[13697.525527] iwlwifi 0000:02:00.0: Status: 0x0004B2E4, count: 6
[13697.525530] iwlwifi 0000:02:00.0: 0x0000198A | ADVANCED_SYSASSERT          
[13697.525532] iwlwifi 0000:02:00.0: 0x00015920 | uPc
[13697.525534] iwlwifi 0000:02:00.0: 0x00015910 | branchlink1
[13697.525536] iwlwifi 0000:02:00.0: 0x00015910 | branchlink2
[13697.525538] iwlwifi 0000:02:00.0: 0x0000DBEA | interruptlink1
[13697.525540] iwlwifi 0000:02:00.0: 0x00000000 | interruptlink2
[13697.525542] iwlwifi 0000:02:00.0: 0x00002A0D | data1
[13697.525544] iwlwifi 0000:02:00.0: 0x00000003 | data2
[13697.525545] iwlwifi 0000:02:00.0: 0x000001DC | line
[13697.525547] iwlwifi 0000:02:00.0: 0xD80020F4 | beacon time
[13697.525549] iwlwifi 0000:02:00.0: 0xFB6A3F0C | tsf low
[13697.525551] iwlwifi 0000:02:00.0: 0x00000002 | tsf hi
[13697.525553] iwlwifi 0000:02:00.0: 0x00000000 | time gp1
[13697.525555] iwlwifi 0000:02:00.0: 0xA8485B00 | time gp2
[13697.525556] iwlwifi 0000:02:00.0: 0x00000000 | time gp3
[13697.525558] iwlwifi 0000:02:00.0: 0x754312A8 | uCode version
[13697.525560] iwlwifi 0000:02:00.0: 0x000000B0 | hw version
[13697.525562] iwlwifi 0000:02:00.0: 0x00480303 | board version
[13697.525564] iwlwifi 0000:02:00.0: 0x0000001C | hcmd
[13697.525566] iwlwifi 0000:02:00.0: CSR values:
[13697.525568] iwlwifi 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[13697.525597] iwlwifi 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[13697.525623] iwlwifi 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[13697.525649] iwlwifi 0000:02:00.0:                     CSR_INT: 0X00000000
[13697.525678] iwlwifi 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[13697.525703] iwlwifi 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[13697.525732] iwlwifi 0000:02:00.0:                 CSR_GPIO_IN: 0X0000003c
[13697.525761] iwlwifi 0000:02:00.0:                   CSR_RESET: 0X00000000
[13697.525786] iwlwifi 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[13697.525812] iwlwifi 0000:02:00.0:                  CSR_HW_REV: 0X000000b0
[13697.525837] iwlwifi 0000:02:00.0:              CSR_EEPROM_REG: 0Xc6aa0ffd
[13697.525863] iwlwifi 0000:02:00.0:               CSR_EEPROM_GP: 0X90000801
[13697.525888] iwlwifi 0000:02:00.0:              CSR_OTP_GP_REG: 0X00030001
[13697.525914] iwlwifi 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[13697.525940] iwlwifi 0000:02:00.0:            CSR_GP_UCODE_REG: 0X0000f65d
[13697.525966] iwlwifi 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[13697.525992] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[13697.526018] iwlwifi 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[13697.526043] iwlwifi 0000:02:00.0:                 CSR_LED_REG: 0X00000078
[13697.526069] iwlwifi 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X88035fcc
[13697.526094] iwlwifi 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[13697.526119] iwlwifi 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[13697.526145] iwlwifi 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[13697.526171] iwlwifi 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[13697.526174] iwlwifi 0000:02:00.0: FH register values:
[13697.526228] iwlwifi 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X028a6e00
[13697.526280] iwlwifi 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00289280
[13697.526337] iwlwifi 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000030
[13697.526382] iwlwifi 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[13697.526438] iwlwifi 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[13697.526472] iwlwifi 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[13697.526515] iwlwifi 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[13697.526564] iwlwifi 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[13697.526599] iwlwifi 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[13697.526679] iwlwifi 0000:02:00.0: Start IWL Event Log Dump: nothing in log
[13697.527366] ieee80211 phy0: Hardware restart was requested
[13697.527524] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[13697.534249] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[13864.112019] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 4c:e6:76:a9:9e:f8 tid = 0
[13864.112052] ------------[ cut here ]------------
[13864.112121] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:1111 iwl_trans_pcie_tx+0x70a/0x750 [iwlwifi]()
[13864.112129] Hardware name: 700Z3A/700Z4A/700Z5A/700Z5B
[13864.112132] Modules linked in: hidp hid samsung_laptop(O) dm_crypt snd_hda_codec_hdmi snd_hda_codec_realtek joydev fglrx(P) arc4 bnep rfcomm parport_pc snd_hda_intel ppdev snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq uvcvideo videodev mei(C) snd_timer snd_seq_device btusb psmouse bluetooth iwlwifi mac_hid serio_raw mac80211 snd cfg80211 soundcore snd_page_alloc binfmt_misc coretemp lp parport i915 drm_kms_helper drm r8169 i2c_algo_bit video
[13864.112231] Pid: 30357, comm: kworker/u:1 Tainted: P         C O 3.2.0-35-generic-pae #55-Ubuntu
[13864.112237] Call Trace:
[13864.112251]  [<c1592027>] ? printk+0x2d/0x2f
[13864.112266]  [<c105a7d2>] warn_slowpath_common+0x72/0xa0
[13864.112294]  [<f941a39a>] ? iwl_trans_pcie_tx+0x70a/0x750 [iwlwifi]
[13864.112318]  [<f941a39a>] ? iwl_trans_pcie_tx+0x70a/0x750 [iwlwifi]
[13864.112328]  [<c105a822>] warn_slowpath_null+0x22/0x30
[13864.112350]  [<f941a39a>] iwl_trans_pcie_tx+0x70a/0x750 [iwlwifi]
[13864.112359]  [<c1054090>] ? try_to_wake_up+0x140/0x190
[13864.112382]  [<f9400375>] ? iwlagn_tx_cmd_build_hwcrypto.isra.12+0x145/0x190 [iwlwifi]
[13864.112405]  [<f940060b>] iwlagn_tx_skb+0x24b/0x450 [iwlwifi]
[13864.112427]  [<f93f7f31>] iwlagn_mac_tx+0xc1/0x130 [iwlwifi]
[13864.112469]  [<f93a8ec4>] __ieee80211_tx+0x64/0x1d0 [mac80211]
[13864.112504]  [<f93aa47e>] ieee80211_tx+0x7e/0xb0 [mac80211]
[13864.112538]  [<f93ab144>] ieee80211_tx_pending+0x74/0x1f0 [mac80211]
[13864.112548]  [<c1061440>] ? local_bh_enable_ip+0x90/0x90
[13864.112556]  [<c1060f63>] tasklet_action+0x63/0x110
[13864.112564]  [<c1061440>] ? local_bh_enable_ip+0x90/0x90
[13864.112571]  [<c10614c1>] __do_softirq+0x81/0x1a0
[13864.112580]  [<c1061440>] ? local_bh_enable_ip+0x90/0x90
[13864.112584]  <IRQ>  [<c1061429>] ? local_bh_enable_ip+0x79/0x90
[13864.112602]  [<c15a7f16>] ? _raw_spin_unlock_bh+0x16/0x20
[13864.112632]  [<f9392eef>] ? ieee80211_agg_tx_operational+0xbf/0x180 [mac80211]
[13864.112643]  [<c11335ea>] ? kmem_cache_free+0xea/0x100
[13864.112653]  [<c14a1c2e>] ? kfree_skbmem+0x2e/0x80
[13864.112681]  [<f9393514>] ? ieee80211_start_tx_ba_cb+0xf4/0x120 [mac80211]
[13864.112713]  [<f939d2ef>] ? ieee80211_iface_work+0x20f/0x310 [mac80211]
[13864.112723]  [<c1074f51>] ? process_one_work+0x101/0x3a0
[13864.112752]  [<f939d0e0>] ? ieee80211_teardown_sdata+0xc0/0xc0 [mac80211]
[13864.112760]  [<c1075a24>] ? worker_thread+0x124/0x2d0
[13864.112768]  [<c1075900>] ? manage_workers.isra.29+0x110/0x110
[13864.112777]  [<c107987d>] ? kthread+0x6d/0x80
[13864.112786]  [<c1079810>] ? flush_kthread_worker+0x80/0x80
[13864.112796]  [<c15af7be>] ? kernel_thread_helper+0x6/0x10
[13864.112802] ---[ end trace 38b47fecba92476d ]---
--------------------------------------------------------------------------

at this point my ability to surf the net,skype,messengers all dissconnect, if i open a terminal at that time and type ping [www.google.com](www.google.com), the terminal just hangs there and says eventually that the host is unreachable.
sometimes it fixes it's self, and sometimes it dosen't and i have to reboot the laptop.

is there anyone that can help?

thank you.

---

### Post by slayt12 on 2012-12-20
What kind of router do you have?

---

### Post by Pjotr123 on 2012-12-20
Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Bad-wireless-connection](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Bad-wireless-connection)
(item 2 and further, right column)

---

