---
title: "Sound problems, seems like it can't find the snd? (Been thru the comprehensive guide)"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by simonwh on 2007-01-27
Hi all!

I recently got tired of windows constant crashes and what else, so I installed Ubuntu on both my laptop and my desktop computer. I got the laptop working flawlessly now, but I got a problem with the desktop computer.

I can't get the sound to work. At the very very beginning (just after the install) it worked through the analog output on my ASUS A8N-SLI Deluxe motherboard. Silly as I was i tried to install some asus drivers or whatever, and now I can't get a sound at all.

I've followed all the steps through the "Comprehensive Sound Problems Solution Guide", and something seems to go wrong under the "Alsa driver Compilation step, using alsa-source".

I think it's under the make and make install part it fails. Look at this: (I'm danish, that's why there's a couple of danish words. Ask me if you need a translation)

```
simon@simon-desktop:/usr/src/modules/alsa-driver$ sudo make
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -auvf include/version.h include/sound/version.h
'include/version.h' -> 'include/sound/version.h'
make dep
make[1]: Går til katalog '/usr/src/modules/alsa-driver'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #9 succeeded at 934 (offset -1 lines).
Hunk #10 succeeded at 981 (offset -1 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #5 succeeded at 2843 with fuzz 2.
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1255 (offset 327 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 321 (offset 29 lines).
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 194 (offset -3 lines).
Hunk #3 succeeded at 778 (offset -9 lines).
Hunk #4 succeeded at 821 (offset -9 lines).
Hunk #5 succeeded at 838 (offset -9 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1341 (offset 25 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #2 succeeded at 165 with fuzz 2.
Hunk #3 succeeded at 366 (offset -4 lines).
Hunk #4 succeeded at 381 (offset -6 lines).
Hunk #5 succeeded at 496 (offset -7 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 995 (offset 26 lines).
Hunk #2 succeeded at 1805 (offset 72 lines).
Hunk #3 succeeded at 1833 (offset 52 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
make[3]: Går til katalog '/usr/src/modules/alsa-driver/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #1 succeeded at 390 (offset 14 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2230 (offset 17 lines).
Hunk #2 succeeded at 2408 (offset 17 lines).
Hunk #3 succeeded at 2535 (offset 17 lines).
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/acore/oss'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #2 succeeded at 2457 (offset 2 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[4]: Går til katalog '/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Forlader katalog '/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Går til katalog '/usr/src/modules/alsa-driver/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #1 succeeded at 207 (offset 13 lines).
Hunk #2 succeeded at 316 (offset 13 lines).
make[4]: Forlader katalog '/usr/src/modules/alsa-driver/acore/seq/oss'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/acore/seq'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/acore'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/i2c'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/i2c/other'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/i2c/other'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/i2c'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/drivers'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/drivers/vx'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/drivers'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/isa'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/gus'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/gus'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/sb'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/sb'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/isa/wavefront'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/isa'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/synth'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/synth/emux'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/synth/emux'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/synth'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/pci'
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 803 (offset 28 lines).
Hunk #2 succeeded at 936 (offset 28 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #1 succeeded at 41 (offset -2 lines).
Hunk #2 succeeded at 738 (offset -11 lines).
Hunk #3 succeeded at 749 (offset -11 lines).
Hunk #4 succeeded at 2824 (offset 11 lines).
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/azx'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/azx'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/trident'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/trident'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pci/vx222'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/pci'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 1914 (offset 3 lines).
Hunk #4 succeeded at 1931 (offset 3 lines).
Hunk #5 succeeded at 3287 (offset -2 lines).
Hunk #6 succeeded at 3308 (offset -2 lines).
Hunk #7 succeeded at 3330 (offset -2 lines).
make[3]: Går til katalog '/usr/src/modules/alsa-driver/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #2 succeeded at 45 with fuzz 1 (offset 2 lines).
Hunk #3 succeeded at 63 (offset 2 lines).
Hunk #4 succeeded at 75 (offset 2 lines).
Hunk #5 succeeded at 119 (offset 2 lines).
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
Hunk #1 succeeded at 1 with fuzz 2.
Hunk #2 succeeded at 177 (offset 27 lines).
Hunk #3 succeeded at 193 (offset 27 lines).
Hunk #4 succeeded at 257 (offset 27 lines).
Hunk #5 succeeded at 271 (offset 27 lines).
Hunk #6 succeeded at 318 (offset 27 lines).
Hunk #7 succeeded at 408 (offset 27 lines).
Hunk #8 succeeded at 428 (offset 27 lines).
Hunk #9 succeeded at 504 (offset 26 lines).
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #1 succeeded at 309 (offset -1 lines).
Hunk #2 succeeded at 351 (offset -1 lines).
Hunk #3 succeeded at 375 (offset -1 lines).
Hunk #4 succeeded at 391 (offset -1 lines).
Hunk #5 succeeded at 678 (offset -3 lines).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/usb/usx2y'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/usb'
make[2]: Går til katalog '/usr/src/modules/alsa-driver/pcmcia'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pcmcia/vx'
copying file alsa-kernel/pcmcia/vx/vxpocket.c
patching file vxpocket.c
copying file alsa-kernel/pcmcia/vx/vx_entry.c
patching file vx_entry.c
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Går til katalog '/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
copying file alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.c
patching file pdaudiocf.c
make[3]: Forlader katalog '/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[2]: Forlader katalog '/usr/src/modules/alsa-driver/pcmcia'
make[1]: Forlader katalog '/usr/src/modules/alsa-driver'
make -C /usr/src/linux-headers-2.6.17-10-generic SUBDIRS=/usr/src/modules/alsa-driver  modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/pci.h:496: error: expected identifier or ‘(’ before numeric constant
/usr/src/modules/alsa-driver/acore/hwdep.c: In function ‘snd_hwdep_dsp_load’:
/usr/src/modules/alsa-driver/acore/hwdep.c:226: warning: implicit declaration of function ‘verify_area’
make[3]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Fejl 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Fejl 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.17-10-generic'
make: *** [compile] Fejl 2
simon@simon-desktop:/usr/src/modules/alsa-driver$ sudo make install
find /lib/modules/2.6.17-10-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Går til katalog '/usr/src/modules/alsa-driver/acore'
mkdir -p /lib/modules/2.6.17-10-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.17-10-generic/kernel/sound/acore
cp: kan ikke udføre stat() 'snd-hwdep.ko': No such file or directory
cp: kan ikke udføre stat() 'snd-page-alloc.ko': No such file or directory
cp: kan ikke udføre stat() 'snd-pcm.ko': No such file or directory
cp: kan ikke udføre stat() 'snd-rawmidi.ko': No such file or directory
cp: kan ikke udføre stat() 'snd-timer.ko': No such file or directory
cp: kan ikke udføre stat() 'snd.ko': No such file or directory
make[1]: *** [modules_install] Fejl 1
make[1]: Forlader katalog '/usr/src/modules/alsa-driver/acore'
make: *** [install-modules] Fejl 1
simon@simon-desktop:/usr/src/modules/alsa-driver$ 

```

I really don't get it. I'm very new to linux, so it's probably a minor detail I'm missing.

I've tried aplay -l and it says
```
aplay: device_list:222: no soundcards found...

```

Thanks for your time!

Best regards,
Simon Henriksen

---

