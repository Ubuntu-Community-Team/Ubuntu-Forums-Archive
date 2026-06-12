---
title: "DVB-C adapter after standby not working"
date: 2009-11-14
forum: Multimedia Software
---

### Post by mirko2324 on 2009-11-14
Hello,

I have a problem with my TV adapter (KNC One TV-Station Plus). An CineView module with an AlphaCrypt card is attached to the TV adapter.

After I wakeup my computer from the standby (suspend to ram or suspend to disk) the tv adapter is not working. If I try to watch tv the screen remains black. After an reboot everything is working fine.

Here is the output of "dmesg | grep -i dvb":
```

[   11.534209] DVB: registering new adapter (KNC1 DVB-C Plus MK3)
[   12.344950] DVB: registering adapter 0 frontend 0 (Philips TDA10023 DVB-C)...
[   17.612243] dvb_ca adapter 0: DVB CAM detected and initialised successfully
[   44.216681] dvb_ca adapter 0: DVB CAM detected and initialised successfully
[  263.547118] dvb_ca adapter 0: CAM tried to send a buffer larger than the link buffer size (65535 > 128)!
[  263.644071] dvb_ca adapter 0: CAM tried to send a buffer larger than the ecount size!
[  263.644083] dvb_ca adapter 0: DVB CAM link initialisation failed :(
[  268.906254] Modules linked in: bridge stp bnep ppdev snd_hda_codec_nvhdmi snd_hda_codec_via tda10023 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss budget_av snd_pcm saa7146_vv snd_seq_dummy videodev snd_seq_oss snd_seq_midi v4l1_compat snd_rawmidi snd_seq_midi_event videobuf_dma_sg snd_seq videobuf_core snd_timer iptable_filter snd_seq_device budget_core nvidia(P) ip_tables snd dvb_core soundcore saa7146 btusb lp x_tables ttpci_eeprom agpgart i2c_nforce2 snd_page_alloc shpchp parport asus_atk0110 usbhid usb_storage r8169 mii
```I have tested it with Ubuntu 9.10, Kubuntu 9.10 and Mythbuntu 9.10!

Can somebody help me?

Thank you in advance ;)

---

### Post by mirko2324 on 2009-11-16
I found a solution for my problem.

I have updated the kernel to version 2.6.32 and now its working without any problem. :D

---

