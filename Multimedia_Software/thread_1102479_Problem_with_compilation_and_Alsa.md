---
title: "Problem with compilation and Alsa"
date: 2009-03-21
forum: Multimedia Software
---

### Post by matmat07 on 2009-03-21
When I try to compile a kernel or something that involve alsa, the process fails. It's the similar result to both, so here's what happen when I try that command
```
CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=386 modules_image
```
```
exec debian/rules  DEBIAN_REVISION=386  INITRD=YES  modules_image 
for module in /usr/src/modules/alsa-driver ; do                       \
          if test -d  $module; then                                \
	    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.27.20" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="x86_64"         \
                             KDREV="386" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
		 read ans;                                        \
              fi;                                                   \
	     );                                                    \
	  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
	  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/alsa-driver'
/usr/bin/make -f debian/rules binary-modules
make[2]: Entering directory `/usr/src/modules/alsa-driver'
/usr/bin/make -j 3 compile
make[3]: Entering directory `/usr/src/modules/alsa-driver'
/usr/bin/make dep
make[4]: Entering directory `/usr/src/modules/alsa-driver'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
make[7]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[7]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[6]: Entering directory `/usr/src/modules/alsa-driver/i2c/l3'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/i2c/l3'
make[6]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[6]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[6]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[6]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[6]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[6]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[6]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[6]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/aw2'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/aw2'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/oxygen'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/oxygen'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[7]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[7]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/at32'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/at32'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/at91'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/at91'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/au1x'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/au1x'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/codecs'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/codecs'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/davinci'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/davinci'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/fsl'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/fsl'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/omap'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/omap'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/pxa'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/pxa'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[6]: Entering directory `/usr/src/modules/alsa-driver/soc/sh'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/soc/sh'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc'
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[6]: Entering directory `/usr/src/modules/alsa-driver/usb/caiaq'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/usb/caiaq'
make[6]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[6]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[4]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[4]: Entering directory `/usr/src/linux-2.6.27'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_wrapper.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/hda_intel.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/hda_codec.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sgbuf.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/hda_proc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/hda_hwdep.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_native.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/hda_generic.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_lib.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_realtek.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_cmedia.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_misc.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_analog.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/timer.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_sigmatel.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_si3054.o
  CC [M]  /usr/src/modules/alsa-driver/acore/wrappers.o
  CC [M]  /usr/src/modules/alsa-driver/acore/misc_driver.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_atihdmi.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_debug.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_conexant.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sound.o
  CC [M]  /usr/src/modules/alsa-driver/pci/hda/patch_via.o
/usr/src/modules/alsa-driver/acore/sound.c: In function ‘snd_request_other’:
/usr/src/modules/alsa-driver/acore/sound.c:100: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/modules/alsa-driver/acore/init.o
/usr/src/modules/alsa-driver/acore/init.c: In function ‘snd_card_register’:
/usr/src/modules/alsa-driver/acore/init.c:568: warning: passing argument 5 of ‘device_create’ makes pointer from integer without a cast
/usr/src/modules/alsa-driver/acore/init.c:568: warning: format not a string literal and no format arguments
  LD [M]  /usr/src/modules/alsa-driver/pci/hda/snd-hda-intel.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/info.o
  CC [M]  /usr/src/modules/alsa-driver/acore/control.o
  CC [M]  /usr/src/modules/alsa-driver/acore/misc.o
/usr/src/modules/alsa-driver/acore/info.c: In function ‘resize_info_buffer’:
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit declaration of function ‘PAGE_ALIGN’
make[6]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[6]: *** Waiting for unfinished jobs....
make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[4]: Leaving directory `/usr/src/linux-2.6.27'
make[3]: *** [compile] Error 2
make[3]: Leaving directory `/usr/src/modules/alsa-driver'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
Module /usr/src/modules/alsa-driver failed.
Hit return to Continue

```

---

### Post by matmat07 on 2009-03-22
More infos: Alsa libs ans utils compiles fine, but not the driver.

---

