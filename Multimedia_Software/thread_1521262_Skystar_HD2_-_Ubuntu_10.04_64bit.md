---
title: "Skystar HD2 - Ubuntu 10.04 64bit"
date: 2010-06-30
forum: Multimedia Software
---

### Post by mas-at on 2010-06-30
Hi,

I´m trying to get my Skystar HD2 running since last week. In between i found a constellation where i can install a driver for the card, get the system booting after it and i´m able to see the card with dmesg.

For that i had to use a newer kernel (2.6.34) because the support for the driver started at 2.6.33-rc6. [1]

So now I´m running a 10.04 AMD64 with the 2.6.34 kernel.

Thats how i have installed the driver:

```

sudo apt-get install build-essential
sudo apt-get install libncurses5-dev
sudo apt-get install mercurial
``````
cd /usr/src
sudo hg clone http://mercurial.intuxication.org/hg/s2-liplianin
sudo ln -s s2-liplianin s2
cd s2-liplianin

sudo make menuconfig
Find Firedtv and remove it, save and exit.
``````
sudo make -j 10
sudo make install
sudo reboot
```after that i was able to see the card with dmesg:

```

mas@agamemnon:~$ dmesg | grep -i dvb
[   17.926167] found a VP-1041 PCI DSS/DVB-S/DVB-S2 device on (07:01.0),
[   17.928976] DVB: registering new adapter (Mantis dvb adapter)
[   18.500885] mantis_frontend_init (0): found STB0899 DVB-S/DVB-S2 frontend @0x68
[   18.501271] DVB: registering adapter 0 frontend 0 (STB0899 Multistandard)...
[   35.865260] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   36.284208] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   36.293115] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   40.942874] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   62.704760] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   62.713509] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   62.799518] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[   62.808407] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[  961.797805] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fbcon tileblit font bitblit softcursor snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi usblp ir_sony_decoder snd_rawmidi ir_jvc_decoder snd_seq_midi_event ir_rc6_decoder snd_seq snd_timer snd_seq_device ir_rc5_decoder p54pci snd ir_nec_decoder p54common soundcore radeon ttm drm_kms_helper lp parport led_class mac80211 cfg80211 drm intel_agp mantis lnbp21 mb86a16 ir_core stb6100 tda10021 psmouse serio_raw snd_page_alloc tda10023 stb0899 stv0299 dvb_core i2c_algo_bit ohci1394 pata_marvell e1000e ieee1394
[  961.797854] Pid: 2326, comm: kdvb-ad-0-fe-0 Tainted: G        W  2.6.34-020634-generic #020634 DG33BU/        
[  961.797890] Process kdvb-ad-0-fe-0 (pid: 2326, threadinfo ffff88020896a000, task ffff880205200000)
[  961.797925]  [<ffffffffa0073290>] ? dvb_frontend_thread+0x0/0x7a0 [dvb_core]
[  961.797942]  [<ffffffffa0071f7c>] dvb_frontend_init+0x2c/0xa0 [dvb_core]
[  961.797948]  [<ffffffffa0073318>] dvb_frontend_thread+0x88/0x7a0 [dvb_core]
[  961.797960]  [<ffffffffa0073290>] ? dvb_frontend_thread+0x0/0x7a0 [dvb_core]
```But now, when i start kaffeine, i get this error, and when i try to make a channel search, kaffeine is freezing.

```

mas@agamemnon:~$ kaffeine
kaffeine(3671) DvbLinuxDevice::identifyDevice: couldn't open "/dev/dvb/adapter0/frontend0" 
kaffeine(3671) DvbManager::loadDeviceManager: successfully loaded "/usr/lib/kde4/kaffeinedvb.so"
```I really hope i can find some help here :)

thx

martin

[1] [http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work](http://linuxtv.org/wiki/index.php/TerraTec_Cinergy_S2_PCI_HD_CI#Making_it_work)

---

