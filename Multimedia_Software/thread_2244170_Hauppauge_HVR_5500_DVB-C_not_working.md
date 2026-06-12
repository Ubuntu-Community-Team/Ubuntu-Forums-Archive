---
title: "Hauppauge HVR 5500 DVB-C not working"
date: 2014-09-14
forum: Multimedia Software
---

### Post by sic2 on 2014-09-14
Hi. 

Im trying to get my Hauppauge HVR 5500 DVB-C working with the new patch released by zzam this week at linuxtv [https://patchwork.linuxtv.org/patch/25867/](https://patchwork.linuxtv.org/patch/25867/) . But I dont know what im doing wrong since im a beginner in linux, tried following this guide on their wiki [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-5500](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-5500) .

This is exactly what I tried:

1.
```
[COLOR=#000000][FONT=monospace]cd ~[/FONT][/COLOR]mkdir get_dvb_firmware
cd get_dvb_firmware
wget [https://raw.github.com/torvalds/linux/master/Documentation/dvb/get_dvb_firmware](https://raw.github.com/torvalds/linux/master/Documentation/dvb/get_dvb_firmware)
chmod a+x get_dvb_firmware
./get_dvb_firmware si2165
./get_dvb_firmware tda10071
sudo cp dvb-demod-si2165.fw /lib/firmware/ [COLOR=#000000][FONT=monospace]sudo cp dvb-fe-tda10071.fw /lib/firmware/[/FONT][/COLOR]
```


2.
```
[COLOR=#444444][FONT=Monaco]git clone git://linuxtv.org/media_build.git[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]cd media_build [/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]./build[/FONT][/COLOR]
```

3.
```
[COLOR=#444444][FONT=Monaco]:~/media_build/linux# patch -p1 < Si2165-Add-experimental-DVB-C-support-for-HVR-4400-HVR-5500.patch[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]patching file drivers/media/dvb-frontends/si2165.c[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]Hunk #1 succeeded at 750 (offset -31 lines).[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]Hunk #2 succeeded at 898 (offset -31 lines).[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]Hunk #3 FAILED at 1053.[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]Hunk #4 succeeded at 1132 (offset -46 lines).[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]1 out of 4 hunks FAILED -- saving rejects to file drivers/media/dvb-frontends/si2165.c.rej[/FONT][/COLOR]
```


and the content of si2165.c.rej is:
```
[COLOR=#444444][FONT=Monaco]si2165.c.rej:[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]--- drivers/media/dvb-frontends/si2165.c[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+++ drivers/media/dvb-frontends/si2165.c[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]@@ -1053,20 +1166,23 @@[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco] static struct dvb_frontend_ops si2165_ops = {[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]        .info = {[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                .name = "Silicon Labs ",[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]-               .caps = FE_CAN_FEC_1_2 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+                /* For DVB-C */[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+               .symbol_rate_min = 870000,[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+               .symbol_rate_max = 11700000,[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+               /* For DVB-T */[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+               .frequency_stepsize = 166667,[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]+               .caps = FE_CAN_FEC_1_2 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_FEC_2_3 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_FEC_3_4 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_FEC_5_6 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_FEC_7_8 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_FEC_AUTO |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]-                       FE_CAN_QPSK |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_QAM_16 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_QAM_32 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_QAM_64 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_QAM_128 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_QAM_256 |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_QAM_AUTO |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]-                       FE_CAN_TRANSMISSION_MODE_AUTO |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_GUARD_INTERVAL_AUTO |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_HIERARCHY_AUTO |[/FONT][/COLOR]
[COLOR=#444444][FONT=Monaco]                        FE_CAN_MUTE_TS |[/FONT][/COLOR]
```

sudo make install

4. sudo dvb-fe-tool --adapter=2 --frontend=0 --set-delsys=DVB-C
```
INFO     Device Silicon Labs Si2165 DVB-T (/dev/dvb/adapter2/frontend0) capabilities:INFO          CAN_FEC_1_2
INFO          CAN_FEC_2_3
INFO          CAN_FEC_3_4
INFO          CAN_FEC_5_6
INFO          CAN_FEC_7_8
INFO          CAN_FEC_AUTO
INFO          CAN_GUARD_INTERVAL_AUTO
INFO          CAN_HIERARCHY_AUTO
INFO          CAN_INVERSION_AUTO
INFO          CAN_MUTE_TS
INFO          CAN_QAM_16
INFO          CAN_QAM_32
INFO          CAN_QAM_64
INFO          CAN_QAM_128
INFO          CAN_QAM_256
INFO          CAN_QAM_AUTO
INFO          CAN_QPSK
INFO          CAN_RECOVER
INFO          CAN_TRANSMISSION_MODE_AUTO
INFO     DVB API Version 5.10, Current v5 delivery system: DVBT
INFO     Supported delivery system: 
INFO         [DVBT]
Changing delivery system to: DVBC/ANNEX_A
ERROR    Set delivery system: Invalid argument
```


dmeg | grep si2165 and cx23885 gives me:

```


SI21665 [    8.873181] i2c i2c-7: si2165: hardware revision 0x03, chip type 0x07[    8.873183] i2c i2c-7: si2165: DVB-C is not yet supported.
[    9.034877] i2c i2c-7: si2165: downloading firmware from file 'dvb-demod-si2165.fw' size=5768
[    9.037986] i2c i2c-7: si2165: si2165_upload_firmware extracted patch_version=0x9a, block_count=0x27, crc_expected=0xcc0a
[   10.149814] i2c i2c-7: si2165: fw load finished

CX23885 [    6.651899] cx23885 driver version 0.0.4 loaded[    6.652016] CORE cx23885[0]: subsystem: 0070:c138, board: Hauppauge WinTV-HVR4400 [card=38,autodetected]
[    6.977697] cx23885[0]: warning: unknown hauppauge model #121029
[    6.977698] cx23885[0]: hauppauge eeprom: model=121029
[    8.863874] cx23885[0]: registered device video0 [v4l2]
[    8.863950] cx23885[0]: registered device vbi0
[    8.864147] cx23885[0]: registered ALSA audio device
[    8.864149] cx23885_dvb_register() allocating 1 frontend(s)
[    8.864150] cx23885[0]: cx23885 based dvb card
[    8.868768] DVB: registering new adapter (cx23885[0])
[    8.868771] cx23885 0000:03:00.0: DVB: registering adapter 1 frontend 0 (NXP TDA10071)...
[    8.869254] cx23885_dvb_register() allocating 1 frontend(s)
[    8.869256] cx23885[0]: cx23885 based dvb card
[    8.873535] DVB: registering new adapter (cx23885[0])
[    8.873537] cx23885 0000:03:00.0: DVB: registering adapter 2 frontend 0 (Silicon Labs Si2165 DVB-T)...
[    8.873749] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    8.873754] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 17, latency: 0, mmio: 0xf7c00000
[   10.154554] cx23885 0000:03:00.0: DVB: adapter 2 frontend 0 frequency 0 out of range (45000000..864000000)
[   14.893409] cx23885 0000:03:00.0: DVB: adapter 1 frontend 0 frequency 0 out of range (950000..2150000)
```

I hope the above information helps. 

Thanks!

---

### Post by sic2 on 2014-09-15
Solved!

---

### Post by CojoteX on 2014-09-18
Same Problem here. How did you solve it?

---

### Post by andreas-renner on 2014-12-23
same situation here, after the guide on linuxtv.org => dvb-t works, dvb-c not.
it seems, that the patch is outdated, at least it fails for me, but i used the c-file supplied by Beta990 - still no success.

can you please give me a hint how you solved the problem?

---

