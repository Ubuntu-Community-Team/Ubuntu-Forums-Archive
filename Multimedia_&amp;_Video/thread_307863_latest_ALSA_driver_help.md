---
title: "latest ALSA driver help"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-11-27
I tried following the description on this page:
[https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard)

I downloaded: alsa-driver-1.0.9b, alsa-firmware-1.0.9, alsa-lib-1.0.9, alsa-util-1.0.9a. And i unpacked them in /home/carsten/alsa. So far no problems.

"make clean" and "make mrproper" gave me some strange info, a lot of entering and exiting folders. But my real problem is with the make command: 
I have a Lexicon Omega soundcard so i use the usb-audio driver. like this:
 ./configure --with-cards=usb-audio --with-oss=yes --with-sequencer=yes
Works fine. now comes trouble:Make leaves 2 errors. 

Can you help me
/Carsten

I dont know what information is important, so i have just copied directly from the terminal:
carsten@carsten-laptop:~/alsa/alsa-driver-1.0.9b$ make
make dep
make[1]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #3 succeeded at 121 (offset -1 lines).
Hunk #4 succeeded at 133 (offset -1 lines).
Hunk #5 succeeded at 143 (offset -1 lines).
Hunk #6 succeeded at 174 (offset -1 lines).
Hunk #7 succeeded at 506 (offset -1 lines).
Hunk #8 succeeded at 519 (offset -1 lines).
Hunk #9 succeeded at 933 (offset -2 lines).
Hunk #10 succeeded at 980 (offset -2 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #2 succeeded at 2750 (offset 2 lines).
Hunk #3 succeeded at 2770 (offset 2 lines).
Hunk #4 succeeded at 2823 (offset 2 lines).
Hunk #5 succeeded at 2850 (offset 2 lines).
Hunk #6 succeeded at 2941 (offset 2 lines).
Hunk #7 succeeded at 2960 (offset 2 lines).
Hunk #8 succeeded at 2978 (offset 2 lines).
Hunk #9 succeeded at 3007 (offset 2 lines).
Hunk #10 succeeded at 3039 (offset 2 lines).
Hunk #11 succeeded at 3068 (offset 2 lines).
Hunk #12 succeeded at 3097 (offset 2 lines).
Hunk #13 succeeded at 3115 (offset 2 lines).
Hunk #14 succeeded at 3135 (offset 2 lines).
Hunk #15 succeeded at 3151 (offset 2 lines).
Hunk #16 succeeded at 3162 (offset 2 lines).
Hunk #17 succeeded at 3193 (offset 2 lines).
Hunk #18 succeeded at 3257 (offset 2 lines).
Hunk #19 succeeded at 3284 (offset 2 lines).
Hunk #20 succeeded at 3325 (offset 2 lines).
Hunk #21 succeeded at 3468 (offset 2 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1259 (offset 3 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1274 (offset 7 lines).
Hunk #2 succeeded at 1357 (offset 7 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 993 (offset -2 lines).
Hunk #2 succeeded at 1842 (offset 51 lines).
Hunk #3 succeeded at 1896 (offset 51 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2088 (offset 16 lines).
Hunk #2 succeeded at 2254 (offset 16 lines).
Hunk #3 succeeded at 2432 (offset 16 lines).
Hunk #4 succeeded at 2564 (offset 16 lines).
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/oss'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[4]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/seq/instr'
make[4]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/seq/instr'
make[4]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/seq/oss'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore/seq'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/acore'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/i2c'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/i2c/other'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/i2c/other'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/i2c'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/pcsp'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/pcsp'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/opl3'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/opl4'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/opl4'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
Hunk #3 succeeded at 62 with fuzz 1.
Hunk #4 succeeded at 89 with fuzz 2 (offset -58 lines).
Hunk #5 succeeded at 241 (offset -6 lines).
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/mpu401'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/vx'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers/vx'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/drivers'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/msnd'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/msnd'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/opti9xx'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/opti9xx'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/ad1816a'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/ad1816a'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/ad1848'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/ad1848'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/cs423x'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/cs423x'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/es1688'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/es1688'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/gus'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/gus'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/opti9xx'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/opti9xx'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/sb'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/sb'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/wavefront'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa/wavefront'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/isa'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/synth'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/synth/emux'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/synth/emux'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/synth'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci'
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 803 (offset 28 lines).
Hunk #2 succeeded at 936 (offset 28 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #1 succeeded at 41 (offset -2 lines).
Hunk #2 succeeded at 748 (offset -1 lines).
Hunk #3 succeeded at 759 (offset -1 lines).
Hunk #4 succeeded at 2863 (offset 50 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/pdplus'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/pdplus'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/pcxhr'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/pcxhr'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/echoaudio'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/echoaudio'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ac97'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ac97'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ali5451'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ali5451'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/au88x0'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/au88x0'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ca0106'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ca0106'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/cs46xx'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/cs46xx'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/emu10k1'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/emu10k1'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/hda'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ice1712'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ice1712'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/korg1212'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/korg1212'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/mixart'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/mixart'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/nm256'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/nm256'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/rme9652'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/rme9652'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/trident'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/trident'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ymfpci'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/ymfpci'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/vx222'
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci/vx222'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pci'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 1882 (offset -26 lines).
Hunk #4 succeeded at 1901 (offset -26 lines).
Hunk #5 succeeded at 1918 (offset -26 lines).
Hunk #6 succeeded at 2452 (offset -26 lines).
Hunk #7 succeeded at 2519 (offset -26 lines).
Hunk #8 succeeded at 2810 (offset -27 lines).
Hunk #9 succeeded at 2880 (offset -27 lines).
Hunk #10 succeeded at 2942 (offset -27 lines).
Hunk #11 succeeded at 2960 (offset -27 lines).
Hunk #12 succeeded at 3118 (offset -8 lines).
Hunk #13 succeeded at 3210 (offset -10 lines).
Hunk #14 succeeded at 3342 (offset -4 lines).
Hunk #15 succeeded at 3373 (offset -4 lines).
Hunk #16 succeeded at 3395 (offset -4 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #2 succeeded at 1650 (offset 1 line).
Hunk #3 succeeded at 1699 (offset 1 line).
Hunk #4 succeeded at 1720 (offset 1 line).
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/usb/usx2y'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/usb'
make[2]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pcmcia'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pcmcia/vx'
copying file alsa-kernel/pcmcia/vx/vxpocket.c
patching file vxpocket.c
Hunk #2 succeeded at 167 (offset -8 lines).
copying file alsa-kernel/pcmcia/vx/vx_entry.c
patching file vx_entry.c
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pcmcia/vx'
make[3]: Går til katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pcmcia/pdaudiocf'
copying file alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.c
patching file pdaudiocf.c
Hunk #3 succeeded at 73 (offset -7 lines).
Hunk #4 succeeded at 180 with fuzz 1 (offset -12 lines).
Hunk #5 succeeded at 266 (offset -13 lines).
Hunk #6 succeeded at 361 (offset -16 lines).
Hunk #7 succeeded at 432 (offset -16 lines).
make[3]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pcmcia/pdaudiocf'
make[2]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b/pcmcia'
make[1]: Forlader katalog '/home/carsten/alsa/alsa-driver-1.0.9b'
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/carsten/alsa/alsa-driver-1.0.9b  modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /home/carsten/alsa/alsa-driver-1.0.9b/acore/hpetimer.o
In file included from /home/carsten/alsa/alsa-driver-1.0.9b/include/adriver.h:677,
                 from /home/carsten/alsa/alsa-driver-1.0.9b/include/sound/driver.h:42,
                 from /home/carsten/alsa/alsa-driver-1.0.9b/acore/hpetimer.c:22:
include/linux/pci.h:496: error: expected identifier or &#8216;(&#8217; before numeric constant
make[3]: *** [/home/carsten/alsa/alsa-driver-1.0.9b/acore/hpetimer.o] Fejl 1
make[2]: *** [/home/carsten/alsa/alsa-driver-1.0.9b/acore] Fejl 2
make[1]: *** [_module_/home/carsten/alsa/alsa-driver-1.0.9b] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.17-10-386'
make: *** [compile] Fejl 2

---

### Post by falkenberg_cph on 2006-11-27
PS: i lost my sound from doing this. ](*,)
seems to be a gstreamer problem. I tried reainstalling both alsa and gstreamer through synaptic package manager. But it didnt help.

---

### Post by falkenberg_cph on 2006-11-27
Ok. i used 1.0.13 drivers and got my usb device up and running. Aparently 1.0.9b was no good. Unfortunately i have not been able to figure out how to install both my usb device and my crappy unboard soundcard "Realtek 97". Can anyone perhaps help me with this?

/Carsten

---

### Post by pljones on 2006-11-28
Are you running Dapper or Edgy?

---

### Post by falkenberg_cph on 2006-11-28
Edgy

---

### Post by pljones on 2006-11-28
I found the ALSA support built into Edgy already had everything necessary (after being disappointed with Dapper).

Have you checked the AC97 page at [the Alsa Project](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+AC97+audio.&chip=440MX%2C+i810%2C+i810E%2C+i820%2C+ICH4%2C+ICH5%2C+ICH6&module=intel8x0) site?

---

### Post by falkenberg_cph on 2006-11-28
I found that too. But unfortunately i had to go and mess with my drivers ](*,)  DONT FIX WHAT IS NOT BROKEN

Anyway, thanks for the link, i looked for it yesterday but couldnt find it (looked for realtek). I will try it later, but it shouldnt cause me problems now.

Thanks
/Carsten

[EDIT]: Later the same day: thank you. it worked fine

---

