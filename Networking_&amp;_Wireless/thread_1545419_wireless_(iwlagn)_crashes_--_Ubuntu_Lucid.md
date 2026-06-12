---
title: "wireless (iwlagn) crashes -- Ubuntu Lucid"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by SaintDanBert on 2010-08-03
I'm running Ubuntu Lucid. My wireless hardware is the Intel 4965 ABGN card.  I'm running the 32-bit PAE kernel v2.6.32-34-generic-pae.

I get the following modules:
```

user@host:/path/$ lsmod | grep i[w]l
iwlagn                106046  0 
iwlcore               106434  1 iwlagn
mac80211              205146  2 iwlagn,iwlcore
cfg80211              126517  3 iwlagn,iwlcore,mac80211
led_class               2864  3 iwlcore,thinkpad_acpi,sdhci
user@host:/path/$

```

The **modinfo iwlagn** reports the driver version as 1.3.27k.

After some random period of time, wifi stops talking. All outward indications say that the workstation remains "connected".  When I look in the **syslog** I see this:
```

iwlagn 0000:03:00.0: Stopping AGG while state not ON or starting
iwlagn 0000:03:00.0: queue number out of range: 0, must be 7 to 14
------------[ cut here ]------------
WARNING: at /build/buildd/linux-2.6.32/net/mac80211/agg-tx.c:150 ___ieee80211_stop_tx_ba_session+0x89/0x90 [mac80211]()

Hardware name: 7764CTO
Modules linked in: aes_i586 aes_generic nls_iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm sco bridge stp bnep l2cap snd_hda_codec_an
alog fbcon tileblit font bitblit softcursor vga16fb vgastate mmc_block snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm thinkpad_acpi snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi arc4 pcmcia snd_seq_midi_event iwlagn snd_seq i915 snd_timer snd_seq_device drm_kms_helper iwlcore drm mac80211 yenta_socket rsrc_nonstatic snd sdhci_pci ppdev intel_agp i2c_algo_bit btusb bluetooth soundcore nvram pcmcia_core sdhci led_class
 cfg80211 psmouse serio_raw tpm_tis snd_page_alloc tpm parport_pc tpm_bios agpgart video output lp parport ohci1394 ieee1394 ahci e1000e

Pid: 9, comm: events/0 Not tainted 2.6.32-24-generic-pae #38-Ubuntu
Call Trace:
[<c0154192>] warn_slowpath_common+0x72/0xa0
[<f87cbf39>] ? ___ieee80211_stop_tx_ba_session+0x89/0x90 [mac80211]
[<f87cbf39>] ? ___ieee80211_stop_tx_ba_session+0x89/0x90 [mac80211]
[<f8d02560>] ? iwl_mac_ampdu_action+0x0/0xd0 [iwlagn]
[<c01541da>] warn_slowpath_null+0x1a/0x20
[<f87cbf39>] ___ieee80211_stop_tx_ba_session+0x89/0x90 [mac80211]
[<f87cc057>] __ieee80211_stop_tx_ba_session+0x57/0x60 [mac80211]
[<f87cb966>] ieee80211_sta_tear_down_BA_sessions+0x26/0x50 [mac80211]
[<f87de8bf>] ieee80211_reconfig+0x1ff/0x430 [mac80211]
[<c0146d73>] ? finish_task_switch+0x43/0xc0
[<f87c743b>] ieee80211_restart_work+0x1b/0x30 [mac80211]
[<c016bbbe>] run_workqueue+0x8e/0x150
[<f87c7420>] ? ieee80211_restart_work+0x0/0x30 [mac80211]
[<c016bd04>] worker_thread+0x84/0xe0
[<c016fc60>] ? autoremove_wake_function+0x0/0x50
[<c016bc80>] ? worker_thread+0x0/0xe0
[<c016f9d4>] kthread+0x74/0x80
[<c016f960>] ? kthread+0x0/0x80
[<c010a4e7>] kernel_thread_helper+0x7/0x10
---[ end trace 61d1f0cc3c5ca79f ]---

wpa_supplicant: Failed to initiate AP scan.
wpa_supplicant: last message repeated 3 times

```

[highlight]Q1: [/highlight] Does anyone have any ideas what I can do about this?

~~~ 0;-Dan

---

