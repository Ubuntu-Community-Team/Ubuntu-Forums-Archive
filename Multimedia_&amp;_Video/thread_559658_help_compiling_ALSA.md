---
title: "help compiling ALSA"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by nitro_n2o on 2007-09-25
Hi all, 
I'm trying to compile alsa for my sound card hda-intel 
however i get some nasty error i have no idea about can some body help me out on this
i configure: 
```
sudo ./configure --with-card=hda-intel
```
```

make dep
make[1]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/acore'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/acore/ioctl32'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/acore/ioctl32'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/acore/oss'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/acore/oss'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/acore/seq'
make[4]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/acore/seq/instr'
make[4]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/acore/seq/instr'
make[4]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/acore/seq/oss'
make[4]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/acore/seq/oss'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/acore/seq'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/acore'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/i2c'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/i2c/other'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/i2c/other'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/i2c'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/drivers'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/mpu401'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/mpu401'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/opl3'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/opl3'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/opl4'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/opl4'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/pcsp'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/pcsp'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/vx'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/drivers/vx'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/drivers'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/ad1816a'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/ad1816a'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/ad1848'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/ad1848'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/cs423x'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/cs423x'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/es1688'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/es1688'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/gus'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/gus'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/msnd'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/msnd'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/opti9xx'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/opti9xx'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/sb'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/sb'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/isa/wavefront'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa/wavefront'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/isa'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/synth'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/synth/emux'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/synth/emux'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/synth'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ac97'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ac97'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ali5451'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ali5451'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/asihpi'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/asihpi'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/au88x0'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/au88x0'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ca0106'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ca0106'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/cs46xx'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/cs46xx'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/cs5535audio'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/cs5535audio'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/echoaudio'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/echoaudio'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/emu10k1'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/emu10k1'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/hda'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/hda'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ice1712'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ice1712'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/korg1212'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/korg1212'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/mixart'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/mixart'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/nm256'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/nm256'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/pcxhr'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/pcxhr'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/pdplus'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/pdplus'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/riptide'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/riptide'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/rme9652'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/rme9652'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/trident'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/trident'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/vx222'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/vx222'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ymfpci'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci/ymfpci'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pci'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/aoa'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/codecs'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/codecs'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/core'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/core'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/fabrics'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/fabrics'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/soundbus'
make[4]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/aoa/soundbus'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/aoa'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/usb'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/usb/usx2y'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/usb/usx2y'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/usb'
make[2]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pcmcia'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/nitro/alsa-driver-1.0.14rc1/pcmcia/vx'
make[3]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pcmcia/vx'
make[2]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1/pcmcia'
make[1]: Leaving directory `/home/nitro/alsa-driver-1.0.14rc1'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/nitro/alsa-driver-1.0.14rc1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/nitro/alsa-driver-1.0.14rc1/acore/pcm.o
In file included from /home/nitro/alsa-driver-1.0.14rc1/acore/../alsa-kernel/core/pcm.c:29,
                 from /home/nitro/alsa-driver-1.0.14rc1/acore/pcm.c:1:
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function ‘snd_pcm_mmap_data_open’:
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h:977: error: dereferencing pointer to incomplete type
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function ‘snd_pcm_mmap_data_close’:
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h:983: error: dereferencing pointer to incomplete type
/home/nitro/alsa-driver-1.0.14rc1/acore/pcm.c: At top level:
/home/nitro/alsa-driver-1.0.14rc1/acore/pcm.c:1: fatal error: opening dependency file /home/nitro/alsa-driver-1.0.14rc1/acore/.pcm.o.d: Permission denied
compilation terminated.
make[3]: *** [/home/nitro/alsa-driver-1.0.14rc1/acore/pcm.o] Error 1
make[2]: *** [/home/nitro/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/nitro/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

``` 
Thx

---

