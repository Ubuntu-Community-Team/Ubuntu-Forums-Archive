---
title: "tired of trying to make sound work in asus m2n-mx......someone plz help"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by sreenidhy on 2007-04-28
Hello everybody

  Recently i installed Feisty Fawn. Initially sound was working[but wud go off after sometime]. I tried to set it right, but was never to be heard again..:( 
  Then i tried [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
[comprehensive guide]....Here under the heading  **Using alsa-source** at step 6, after i tried ***sudo make***, this is wat i got....
   

> [I]sree@desktop:/usr/src/modules/alsa-driver$ sudo make
make dep
make[1]: Entering directory `/usr/src/modules/alsa-driver'
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[2]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
[B]make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2[/B]
[/I]




The bolded region is where the error starts....
Can someone tell me wat error is this..
   My pc:
               mobo : asus m2n-mx
               processor : athlon x2 3600+
               ram : 1gb ddr
               onboard video : nvidia geforce 6100
               onboard audio : ADI AD1986A

---

### Post by [S2] on 2007-05-04
> In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1: /usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
You need to install the kernel headers.

---

