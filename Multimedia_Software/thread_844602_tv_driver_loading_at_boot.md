---
title: "tv driver loading at boot"
date: 2008-06-29
forum: Multimedia Software
---

### Post by gh81 on 2008-06-29
Hi,

Someone gave me a TV tuner card, and after a lot of trouble, I have finally got it to work in linux... almost. To cut a long story short, I am using the video4linux drivers for the saa7134 chipset. I've edited /etc/modules to load saa7134 and saa7134_dvb at boot, and they do load. The trouble is, to get any kind of TV signal in any application, I have to first unload these drivers and then reload them:

rmmod saa7134_dvb
rmmod saa7134
modprobe saa7134
modprobe saa7134_dvb

and then everything works fine. The results of dmesg | grep saa7134 after boot, before reloading the drivers is:

```
[   52.761108] saa7134[0]: found at 0000:01:08.0, rev: 1, irq: 9, latency: 32, mmio: 0xee000000
[   52.761114] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]
[   52.761123] saa7134[0]: board init: gpio is 841f00
[   52.761194] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:08.0/0000:01:08.0/input/input6
[   52.940207] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   52.940218] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   52.940225] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   52.940232] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940238] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   52.940245] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   52.940252] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940258] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940265] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940272] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940278] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940285] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940292] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940298] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940305] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   52.940311] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.139884] tuner' 2-0043: chip found @ 0x86 (saa7134[0])
[   53.187601] tuner' 2-0068: chip found @ 0xd0 (saa7134[0])

```


and after reloading:

```

[ 4173.184855] saa7134[0]: found at 0000:01:08.0, rev: 1, irq: 9, latency: 32, mmio: 0xee000000
[ 4173.184863] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]
[ 4173.184872] saa7134[0]: board init: gpio is 841f00
[ 4173.185394] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:08.0/0000:01:08.0/input/input9
[ 4173.346464] tuner' 2-0043: chip found @ 0x86 (saa7134[0])
[ 4173.360782] tuner' 2-0061: chip found @ 0xc2 (saa7134[0])
[ 4173.368933] tuner' 2-0068: chip found @ 0xd0 (saa7134[0])
[ 4173.419528] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 4173.419541] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[ 4173.419548] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[ 4173.419555] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419562] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[ 4173.419568] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[ 4173.419575] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419582] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419589] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419595] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419602] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419609] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419615] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419622] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419629] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.419635] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 4173.565202] saa7134[0]: registered device video0 [v4l2]
[ 4173.565226] saa7134[0]: registered device vbi0
```


The only difference seems to be that it finds 3 tuners instead of 2 after reloading (I don't know how many it's supposed to have, but anyway I only seem to be able to use one). It always creates /dev/video0 and /dev/vbi0.

Any ideas why this is happening? It's a pain to have to reload the drivers every time I boot up.

---

