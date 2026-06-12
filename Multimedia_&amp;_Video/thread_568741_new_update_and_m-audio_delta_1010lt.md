---
title: "new update and m-audio delta 1010lt"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by mynis on 2007-10-06
ok so i just installed the updates (using fiesty 7.04) that were available because it didn't look like anything major. upon restarting i couldn't boot my gui. i got that figured out but after that my sound wasn't working. read practically every thread none of the solutions have worked except once i got the startup noise to play. odd thing is i've been using fiesty since it came out and never had to configure it at all to get my sound working before, i just installed alsa and disabled my on board sound card and it started working. anyways now when i try and run a test in the sound preferences pannel i get this message > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
when i hit the play button in xmms i get > failed to open audio output: ALSA 1.2.10 output plugin
when i typed in "aplay -l" i got the following results:
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

i've also had some trouble trying to manually alter the drivers. i can re install also in synaptic and stuff but i tried following the instructions [here]("http://ubuntuforums.org/showthread.php?t=205449") and i keep getting stuck in step 6 of the "ALSA driver compilation" section. if i try and do it with the module assistant my comp just crashes. when i do it manually the ./configure works fine but when i go to make  i get a bunch of errors like:
```
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
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2


```

i'm not very fluent in linux (as you can probably tell) but it doesn't realy seem like the answer to this should be all that complicated considering it worked fine right out of the box without any tweaking before i installed that update last night. any tips will be greatly apreciated

---

### Post by Tom Mann on 2007-10-17
You may want to try:

```
asoundconf list
asoundconf set-default-card [card name as listed in the response you get from asoundconf list]
```

(I'm guessing it would be as follows)
```
asoundconf set-default-card M1010LT
```

You may have to restart alsa:

```
sudo /etc/init.d/alsa-base restart
```

---

