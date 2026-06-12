---
title: "Wintv-HVR-1120 woes"
date: 2010-10-21
forum: Mythbuntu
---

### Post by demiurg on 2010-10-21
I'm having all sorts of troubles with Wintv-HVR-1120 on Ubuntu 10.10 (kernel 2.6.35-22). Judging from what I've seen on the net, including this mailing list, I'm not the only one not being able to use this card and no solution seem to exist.

Problems:
1. The driver yells various cryptic error messages
("tda18271_write_regs: [1-0060|M] ERROR: idx = 0x5, len = 1,
i2c_transfer returned: -5", "tda18271_set_analog_params: [1-0060|M]
error -5 on line 1045", etc)
2. DVB-T scan (using w_scan) produces no results
3. Analog seems to work, but with very poor quality

Any suggestions would be greatly appreciated.

---

### Post by demiurg on 2010-10-22
In addition, during analog scan, I get the following errors:

[ 6327.420037] tda18271c2_rf_tracking_filters_correction: [1-0060|M] error -22 on line 278
[ 6327.468028] tda18271_calc_ir_measure: [1-0060|M] error -34 on line 716
[ 6327.468074] tda18271_calc_bp_filter: [1-0060|M] error -34 on line 648
[ 6327.468117] tda18271_calc_rf_band: [1-0060|M] error -34 on line 682
[ 6327.468159] tda18271_calc_gain_taper: [1-0060|M] error -34 on line 699

---

### Post by ftirapelle on 2010-10-22
I have similar problems

The WinTV did work correctly with ubuntu 9.10. In Ubuntu 9.10 the package linux-firmware-nonfree didn't include the dvb-fe-tda10048-1.0.fw. I remember that Ubuntu 9.10 used for my card the dvb-fe-tda10046.fw.
Now, Ubuntu 10.04 loads for my card the dvb-fe-tda10048-1.0.fw
Why?

I get random the following errors:

```

[  53.216153] DVB: registering new adapter (saa7133[0])
[  53.216156] DVB: registering adapter 2 frontend 0 (NXP TDA10048HN DVB-T)...
[  53.840013] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[  53.840019] saa7134 0000:01:06.0: firmware: requesting dvb-fe-tda10048-1.0.fw
[  53.880505] tda10048_firmware_upload: firmware read 24878 bytes.
[  53.880509] tda10048_firmware_upload: firmware uploading
[  58.280136] tda10048_firmware_upload: firmware uploaded
[  59.024537] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[  59.024541] tda18271c2_rf_tracking_filters_correction: error -5 on line 264
[  59.420153] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[  59.420157] tda18271_toggle_output: error -5 on line 47
[  91.004019] Clocksource tsc unstable (delta = -295012684 ns)
[  256.293639] eth0: link up.
[  256.294750] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  263.523498] eth0: link down.
[  265.258740] eth0: link up.
[  266.460026] eth0: no IPv6 routers present
[ 9869.636167] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[ 9869.636178] tda18271_init: error -5 on line 826
[ 9872.636220] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[ 9872.636232] tda18271_toggle_output: error -5 on line 47
[ 9998.240167] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[ 9998.240178] tda18271_init: error -5 on line 826
[10001.240179] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[10001.240190] tda18271_toggle_output: error -5 on line 47

```

---

### Post by demiurg on 2010-10-22
I reported it on the linux-media mailing list but got no response. Maybe you should do the same - if more people report this issue maybe some of the developers will notice.

---

### Post by ftirapelle on 2010-10-22
In too. Subject: Hauppauge WinTV-HVR-1120 on Unbuntu 10.04

---

### Post by demiurg on 2010-10-23
I guess we are stuck. 
I'm considering to buy a different card, but there is no way to know which one will work on Linux - this one was supposed to be OK...

---

### Post by ftirapelle on 2010-10-25
Hi

I have no problems with the Hauppauge NOTA-T (usb): [http://www.hauppauge.co.uk/site/products/data_novatstick.html](http://www.hauppauge.co.uk/site/products/data_novatstick.html)
I have bought 2 of this sticks as my WinTV-1120 doesn't work.

---

### Post by demiurg on 2010-10-25
I'd rather use PCI card as my media center is a low power Atom based system...

---

### Post by ftirapelle on 2010-10-25
As I have written in the last thread of [email]linux-media@vger.kernel.org[/email] (subject: Wintv-HVR-1120 woes) my WinTV-HVR-1120 works if I delete dvb-fe-tda10048-1.0.fw and rename dvb-fe-tda10046.fw in dvb-fe-tda10048-1.0.fw.
After reboot my WinTV-HVR-1120 works. Ubuntu recognizes that the firmware isn't correct and doesn't load the firmware.
But I know that isn't a good practice!

---

### Post by demiurg on 2010-10-25
I'm the guy you are exchanging emails on the mailing list :)

I tried to replace the firmware as you suggested, but it have not change a thing - I still get the same errors and scan still does not work. BTW, did you try to scan with this firmware trick ?

---

### Post by ftirapelle on 2010-10-25
lol :P

I post even the same question, hoping that somebody can help us.

The WinTV-1120 did work correctly with Ubunt 9.10. I haven't had problems with this version of Ubuntu. But the linux-firmware-nonfree package for Ubuntu 9.10 (karmic) didn't contain the dvb-fe-tda10048-1.0.fw
(see [http://packages.ubuntu.com/karmic/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/karmic/all/linux-firmware-nonfree/filelist))
The dvb-fe-tda10048-1.0.fw was introduced with lucid (see [http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist)).
And now the question. Why without dvb-fe-tda10048-1.0.fw I haven't had problems and now with Ubuntu 10.04 I have problems exactly with this firmware?

---

### Post by ftirapelle on 2010-10-26
I have tried again.

```

rm -i dvb-fe-tda10048-1.0.fw
cp dvb-fe-tda10046.fw dvb-fe-tda10048-1.0.fw

```

reboot

dmesg

```

[   47.724011] tda18271: RF tracking filter calibration complete
[   47.780018] tda829x 8-004b: type set to tda8290+18271
[   52.756163] saa7133[0]: registered device video0 [v4l2]
[   52.756260] saa7133[0]: registered device vbi0
[   52.756312] saa7133[0]: registered device radio0
[   52.774804] saa7134 ALSA driver for DMA sound loaded
[   52.774818] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   52.774837] saa7133[0]/alsa: saa7133[0] at 0xfcfff800 irq 16 registered as card -2
[   52.826225] dvb_init() allocating 1 frontend
[   53.176016] tda829x 8-004b: type set to tda8290
[   53.216128] tda18271 8-0060: attaching existing instance
[   53.216133] DVB: registering new adapter (saa7133[0])
[   53.216137] DVB: registering adapter 3 frontend 0 (NXP TDA10048HN DVB-T)...
[   53.744012] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   53.744470] saa7134 0000:01:06.0: firmware: requesting dvb-fe-tda10048-1.0.fw
[   53.789956] tda10048_firmware_upload: firmware read 24478 bytes.
[   53.789959] tda10048_firmware_upload: firmware incorrect size
[   53.789963] tda10048_firmware_upload: firmware upload failed
[   55.240026] tda18271_read_regs: ERROR: i2c_transfer returned: -5
[   55.852518] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
[   55.852526] tda18271_set_analog_params: error -5 on line 1041
[   91.004017] Clocksource tsc unstable (delta = -308694953 ns)
[  810.460024] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[  810.460039] saa7134 0000:01:06.0: firmware: requesting dvb-fe-tda10048-1.0.fw
[  810.463999] tda10048_firmware_upload: firmware read 24478 bytes.
[  810.464081] tda10048_firmware_upload: firmware incorrect size
[  810.464091] tda10048_firmware_upload: firmware upload failed

```

now my WinTv-1120 works

---

### Post by wolram173 on 2010-11-01
I have also problem with the Wintv-HVR-112o.

I got this dmesg:

[   60.860016] tda829x 0-004b: type set to tda8290+18271
[   69.050198] saa7133[0]: registered device video0 [v4l2]
[   69.050266] saa7133[0]: registered device vbi0
[   69.050330] saa7133[0]: registered device radio0
[   69.053174] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   69.053179] saa7134_alsa: Unknown symbol snd_ctl_add
[   69.053280] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   69.053283] saa7134_alsa: Unknown symbol snd_pcm_new
[   69.053470] saa7134_alsa: disagrees about version of symbol snd_card_register
[   69.053473] saa7134_alsa: Unknown symbol snd_card_register
[   69.053661] saa7134_alsa: disagrees about version of symbol snd_card_free
[   69.053663] saa7134_alsa: Unknown symbol snd_card_free
[   69.053846] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   69.053848] saa7134_alsa: Unknown symbol snd_pcm_stop
[   69.054049] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   69.054051] saa7134_alsa: Unknown symbol snd_ctl_new1
[   69.054605] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   69.054607] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   69.054898] saa7134_alsa: disagrees about version of symbol snd_ctl_notify
[   69.054900] saa7134_alsa: Unknown symbol snd_ctl_notify
[   69.054992] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   69.054994] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   69.055281] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   69.055284] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   69.055713] saa7134_alsa: disagrees about version of symbol snd_card_create
[   69.055716] saa7134_alsa: Unknown symbol snd_card_create
[   69.055806] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   69.055809] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   69.055899] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   69.055902] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   69.133158] dvb_init() allocating 1 frontend
[   69.710017] tda829x 0-004b: type set to tda8290
[   70.091840] tda18271 0-0060: attaching existing instance
[   70.091847] DVB: registering new adapter (saa7133[0])
[   70.091850] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   71.390018] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   71.390026] saa7134 0000:04:01.0: firmware: requesting dvb-fe-tda10048-1.0.fw
[   71.431590] tda10048_firmware_upload: firmware read 24878 bytes.
[   71.431594] tda10048_firmware_upload: firmware uploading
[   73.377034] lirc_imon: IR port closed
[   77.340024] tda10048_firmware_upload: firmware uploaded
[   78.870042] tda18271_write_regs: ERROR: idx = 0x1, len = 7, i2c_transfer returned: -5
[   78.870049] tda18271_channel_configuration: error -5 on line 184
[   78.870056] tda18271_set_analog_params: error -5 on line 1041
[   80.443554] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   80.443560] saa7134_alsa: Unknown symbol snd_ctl_add
[   80.443705] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   80.443708] saa7134_alsa: Unknown symbol snd_pcm_new
[   80.443978] saa7134_alsa: disagrees about version of symbol snd_card_register
[   80.443981] saa7134_alsa: Unknown symbol snd_card_register
[   80.444250] saa7134_alsa: disagrees about version of symbol snd_card_free
[   80.444254] saa7134_alsa: Unknown symbol snd_card_free
[   80.444516] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   80.444519] saa7134_alsa: Unknown symbol snd_pcm_stop
[   80.444807] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   80.444810] saa7134_alsa: Unknown symbol snd_ctl_new1
[   80.445605] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   80.445608] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   80.446024] saa7134_alsa: disagrees about version of symbol snd_ctl_notify
[   80.446027] saa7134_alsa: Unknown symbol snd_ctl_notify
[   80.446158] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   80.446161] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   80.446573] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   80.446577] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   80.447192] saa7134_alsa: disagrees about version of symbol snd_card_create
[   80.447195] saa7134_alsa: Unknown symbol snd_card_create
[   80.447324] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   80.447327] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   80.447457] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[   80.447461] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   82.227737] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 648
[   84.360030] tda18271_write_regs: ERROR: idx = 0x13, len = 1, i2c_transfer returned: -5

What to do?

---

### Post by demiurg on 2010-11-01
No idea. It looks like the developers are not interested in making this card work. I'd it myself, I'm willing to invest some time in debugging this, but as I'm completely unfamiliar with the source code of this project, it will take me weeks if not months...

---

### Post by demiurg on 2010-11-01
I booted into Ununtu 9.10 live CD for the sake of experiment just to discover that the same problem existed in 9.10 as well

---

### Post by tof06 on 2010-11-03
Hi, 

I'm not a Mythbuntu user, but I'm using MythTV on a Gentoo system (kernel 2.6.36, with TuxOnIce patches), and I have a HVR 1120 card.

I do have the same errors as you in dmesg :
```

[    9.312500] saa7130/34: v4l2 driver version 0.2.16 loaded
[    9.312560] saa7134 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.312642] saa7133[0]: found at 0000:04:02.0, rev: 209, irq: 18, latency: 32, mmio: 0xfbcff000
[    9.312648] saa7133[0]: subsystem: 0070:6707, board: Hauppauge WinTV-HVR1120 DVB-T/Hybrid [card=156,autodetected]
[    9.312684] saa7133[0]: board init: gpio is 40000
[...]
[    9.465626] tveeprom 8-0050: Hauppauge model 67209, rev C2F5, serial# 6560239
[    9.465628] tveeprom 8-0050: MAC address is 00:0d:fe:64:19:ef
[    9.465630] tveeprom 8-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[    9.465633] tveeprom 8-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[    9.465635] tveeprom 8-0050: audio processor is SAA7131 (idx 41)
[    9.465637] tveeprom 8-0050: decoder processor is SAA7131 (idx 35)
[    9.465639] tveeprom 8-0050: has radio, has IR receiver, has no IR transmitter
[    9.465640] saa7133[0]: hauppauge eeprom: model=67209
[    9.482600] tuner 8-004b: chip found @ 0x96 (saa7133[0])
[    9.518468] tda829x 8-004b: setting tuner address to 60
[    9.545841] tda18271 8-0060: creating new instance
[    9.574459] TDA18271HD/C2 detected @ 8-0060
[   10.357360] tda18271: performing RF tracking filter calibration
[   21.079980] tda18271: RF tracking filter calibration complete
[   21.108980] tda829x 8-004b: type set to tda8290+18271
[   24.498610] saa7133[0]: registered device video0 [v4l2]
[   24.498652] saa7133[0]: registered device vbi0
[   24.498698] saa7133[0]: registered device radio0
[   24.576891] dvb_init() allocating 1 frontend
[   24.611529] tda829x 8-004b: type set to tda8290
[   24.615638] tda18271 8-0060: attaching existing instance
[   24.615642] DVB: registering new adapter (saa7133[0])
[   24.615644] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   24.725513] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   24.728314] tda10048_firmware_upload: firmware read 24878 bytes.
[   24.728316] tda10048_firmware_upload: firmware uploading
[   28.743022] tda10048_firmware_upload: firmware uploaded
[...]
[B][   45.663852] tda18271_write_regs: [8-0060|M] ERROR: idx = 0x25, len = 1, i2c_transfer returned: -5
[   45.663858] tda18271_channel_configuration: [8-0060|M] error -5 on line 119
[   45.663862] tda18271_set_analog_params: [8-0060|M] error -5 on line 1045[/B]

```Anyway, my card works, at least, in DVB-T mode. I didn't test analog mode.

To make it scan correctly, I had to modify the initial scan file. I'm located in France, and I'm using the fr-Cannes file. I had to add 188 KHz to each transponder frequency.
E.g., for the multiplex R1, the initial file give :
```

#R1
T 490000000 8MHz AUTO NONE QAM64 8k AUTO NONE

```I modified it like :

```

#R1
T 490188000 8MHz AUTO NONE QAM64 8k AUTO NONE

```When I run dvbscan, all multiplex (except R5 but it's not emitted in my region) are correctly scanned. 

I tried several recording with mythtv, and don't get any problem.
I rarely reboot the mythbox, but rather suspend it (S3).
The remote control never worked, but I'm not using it since I've a USB-UIRT IR module.

---

### Post by theanthony33 on 2010-12-08
> **tof06 said:**
> Hi, 

I'm not a Mythbuntu user, but I'm using MythTV on a Gentoo system (kernel 2.6.36, with TuxOnIce patches), and I have a HVR 1120 card.

I do have the same errors as you in dmesg :
```

[    9.312500] saa7130/34: v4l2 driver version 0.2.16 loaded
[    9.312560] saa7134 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.312642] saa7133[0]: found at 0000:04:02.0, rev: 209, irq: 18, latency: 32, mmio: 0xfbcff000
[    9.312648] saa7133[0]: subsystem: 0070:6707, board: Hauppauge WinTV-HVR1120 DVB-T/Hybrid [card=156,autodetected]
[    9.312684] saa7133[0]: board init: gpio is 40000
[...]
[    9.465626] tveeprom 8-0050: Hauppauge model 67209, rev C2F5, serial# 6560239
[    9.465628] tveeprom 8-0050: MAC address is 00:0d:fe:64:19:ef
[    9.465630] tveeprom 8-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[    9.465633] tveeprom 8-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[    9.465635] tveeprom 8-0050: audio processor is SAA7131 (idx 41)
[    9.465637] tveeprom 8-0050: decoder processor is SAA7131 (idx 35)
[    9.465639] tveeprom 8-0050: has radio, has IR receiver, has no IR transmitter
[    9.465640] saa7133[0]: hauppauge eeprom: model=67209
[    9.482600] tuner 8-004b: chip found @ 0x96 (saa7133[0])
[    9.518468] tda829x 8-004b: setting tuner address to 60
[    9.545841] tda18271 8-0060: creating new instance
[    9.574459] TDA18271HD/C2 detected @ 8-0060
[   10.357360] tda18271: performing RF tracking filter calibration
[   21.079980] tda18271: RF tracking filter calibration complete
[   21.108980] tda829x 8-004b: type set to tda8290+18271
[   24.498610] saa7133[0]: registered device video0 [v4l2]
[   24.498652] saa7133[0]: registered device vbi0
[   24.498698] saa7133[0]: registered device radio0
[   24.576891] dvb_init() allocating 1 frontend
[   24.611529] tda829x 8-004b: type set to tda8290
[   24.615638] tda18271 8-0060: attaching existing instance
[   24.615642] DVB: registering new adapter (saa7133[0])
[   24.615644] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   24.725513] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
[   24.728314] tda10048_firmware_upload: firmware read 24878 bytes.
[   24.728316] tda10048_firmware_upload: firmware uploading
[   28.743022] tda10048_firmware_upload: firmware uploaded
[...]
[B][   45.663852] tda18271_write_regs: [8-0060|M] ERROR: idx = 0x25, len = 1, i2c_transfer returned: -5
[   45.663858] tda18271_channel_configuration: [8-0060|M] error -5 on line 119
[   45.663862] tda18271_set_analog_params: [8-0060|M] error -5 on line 1045[/B]

```Anyway, my card works, at least, in DVB-T mode. I didn't test analog mode.

To make it scan correctly, I had to modify the initial scan file. I'm located in France, and I'm using the fr-Cannes file. I had to add 188 KHz to each transponder frequency.
E.g., for the multiplex R1, the initial file give :
```

#R1
T 490000000 8MHz AUTO NONE QAM64 8k AUTO NONE

```I modified it like :

```

#R1
T 490188000 8MHz AUTO NONE QAM64 8k AUTO NONE

```When I run dvbscan, all multiplex (except R5 but it's not emitted in my region) are correctly scanned. 

I tried several recording with mythtv, and don't get any problem.
I rarely reboot the mythbox, but rather suspend it (S3).
The remote control never worked, but I'm not using it since I've a USB-UIRT IR module.

Hi,

How did you find that you must add 188KHz to all frequencies ? My card can't find any channels, but the mythtv scan show a signal strenth between 75 to 90%. I tried to add 188Khz to all frequencies but have the same problem. I scan with me-tv. I use fr-Arcachon file.

Thanks

---

### Post by tof06 on 2010-12-10
I don't remember where I found that exactly.
I remember I booted up Windows and launch WinTV application. When WinTV Scan frequencies, it removes some KHz (don't remember how many) and add some other for each freq... I write down theses offset, and tried in Linux.

---

### Post by mmanzato on 2011-01-11
Back to the original subject, on Mythbuntu 10.10 problems with TDA18271 errors persist. I've also joined the linux-media mailing list. A week ago I've also e-mailed directly to who I suppose to be the mantainer of the driver, but I got no response so far.

I can confirm that my card does NOT work if I rename the firmware of TDA10046 to TDA10048. However the firmware which ships in the linux-firmware-nonfree package seems to be loaded correctly.

I'll try to boot 9.04 live in order to test whether the driver was working ~2 years ago.

Others ([http://www.kernellabs.com/blog/?p=299](http://www.kernellabs.com/blog/?p=299)) suggest that unloading and reloading the driver with a rmmod saa7134_dvb and modprobe saa7134_dvb solve the problem. I'll have a try.

Cheers
Michele

---

### Post by mmanzato on 2011-01-12
Well, I can confirm that on my system unloading and reloading the driver solves the problem.

So, in conclusion:
- install tda10048 firmware from linux-firmware-nonfree Ubuntu package
- rmmod saa7134_dvb 
- modprobe saa7134_dvb

Probably that happens because the Saa starts using the tda before firmware upload completes, in fact the first errors are spit out in between.

Unfortunately this does not always work. Sometimes the firmware is not loaded correctly, and hence rmmod/modprobe doesn't fix things up.

Things might get better if I could find a way to postpone loading of the SAA driver after the tda10048 driver has fully loaded its firmware.

M

---

