---
title: "Problems updating alsa"
date: 2011-05-04
forum: Multimedia Software
---

### Post by BcRich on 2011-05-04
Hi 
I'm using ubuntu 10.04 and am still pretty clueless when it comes to compiling software. my sound has just completely stopped working and I've tried just about everything to get it working again, but have had no luck. I came across this post [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) which seemed to suggest that I need to update to alsa version 1.0.23. however when it came to the 
sudo make
command I get this error
```
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make[4]: Nothing to be done for `prepare2'.
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/include/sound'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/include'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/ioctl32'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/oss'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq/oss'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/acore'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/i2c'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/l3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/l3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/other'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/i2c/other'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/i2c'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/sb'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wavefront'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wavefront'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa/wss'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ac97'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ali5451'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/au88x0'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/aw2'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/aw2'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ca0106'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ctxfi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/hda'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/korg1212'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/lx6464es'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/oxygen'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/oxygen'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/riptide'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ymfpci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/atmel'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/atmel'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/au1x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/au1x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/blackfin'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/blackfin'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/davinci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/davinci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/fsl'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/fsl'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/imx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/imx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/omap'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/omap'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/pxa'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/pxa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s3c24xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s6000'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/s6000'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/sh'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/sh'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/soc/txx9'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc/txx9'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/soc'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/caiaq'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/caiaq'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/misc'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/misc'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/usb/usx2y'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/pcmcia'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.23/misc'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23/misc'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.23'
make -C /lib/modules/2.6.35-020635rc1-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.23  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-020635rc1-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/memalloc.o
  CC [M]  /usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-020635rc1-generic'
make: *** [compile] Error 2
```
does anyone know what it means and how i can fix it. it would be such a waste of bandwidth if this does not work out for me becasue following the instructions on the listed post required me having to download about 300MB of data :(
please help me if you can, many thanks

---

### Post by lidex on 2011-05-05
That's not the latest version of alsa and the method posted on that page is not for noobs. 
I always recommend the alsa upgrade script linked to in my sig. Now why do you think you need the upgrade?

---

### Post by BcRich on 2011-05-06
hi lidex
you're right about that, definitely not recommended for noobs (like myself) :)
the main reason i'd like to upgrade alsa is because i've tried just about everything else to get audio working (again because it used to) on ubuntu 10.04 and nothing has helped.
in short, it's a last resort.
thanks for your suggestion regarding the update script, i'll hold out on that option for a while. (this is me hoping that someone might have a better suggestion).
thanks again, your help has been very much appreciated :)

---

### Post by BcRich on 2011-05-06
i tried the upgrade script and it all seemed to work. but when i run aplay -l
my sound card does not show up? here's what does:
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
 my sound card is an external lexicon omega usb
lsusb prints this 
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1210:0002  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 12d1:1464 Huawei Technologies Co., Ltd. 
Bus 001 Device 007: ID 1e3d:2095  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
as you can see my soundcard is not showing up there either
and cat /proc/asound/cards does not show my soundcard either
```
0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xbfffc000 irq 17
 1 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0x9c00, irq 16

```
i still have no sound, but i know the sound card works fine on this computer as i also have ubuntu 9.04 installed on the same machine, and the soudn card works fine in that version?

---

### Post by lidex on 2011-05-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Yellow Pasque on 2011-05-06
If it's not showing in lsusb, then the problem goes deeper than alsa.. Not really sure what to suggest though.

---

### Post by lidex on 2011-05-06
Hmm, try this:
> If the Omega is not appearing properly you may need to reset the unit.
To do this disconnect the USB and power cables from the Omega then simultaneously press and hold the 1st and 3rd USB Assign buttons (one between the Mic 1 and Mic 2, the other between Line 3 and Line 4) and reconnect the power cable to the back of the Omega. Continue to hold the USB Assign buttons for until the LED’s between the Line 1 and Line 2 knobs flash then release the buttons and reconnect the USB cable. 

---

### Post by BcRich on 2011-05-07
hi 
I'm still having no luck with the sound, that is to say I don't have any sound in ubuntu 10.04 at all.
here's the link to my alsa info 
Your ALSA information is located at  [URL="http://www.alsa-project.org/db/?f=117d05a95d42de5112f552666efa40e4dc69662a"]http://www.alsa-project.org/db/?f=117d05a95d42de5112f552666efa40e4dc69662a
[/URL] something that might help?
when the problem started occurring a while back I had an error message while ubuntu was starting up it read something to the effect of "invalid index (or option) for snd-usb-audio, press i to ignore f to fix"
I pressed i several times to ignore the problem an ubuntu would continue to boot, but I'd have no sound. then the next time I rebooted I'd get the same error message. Until I pressed f on one occassion and the message stops appearing when I boot ubuntu. sorry, I cannot remember the exact wording of the error message as I have not seen in some time.
my etc/modprobe.d/alsa-base.conf looks like this,
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd_usb_audio
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
#options snd-usb-audio index=-2
options snd-usb-us122l index=-2
#options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```
and here's the results of running the boot info script linked in lidex sig, (don't know if that's going to help?)
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,008,269   613,008,207  83 Linux
/dev/sda2         613,008,270   625,137,344    12,129,075   5 Extended
/dev/sda5         613,008,333   625,137,344    12,129,012  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   964,702,207   964,700,160  83 Linux
/dev/sdb2         964,704,254   976,773,119    12,068,866   5 Extended
/dev/sdb5         964,704,256   976,773,119    12,068,864  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2143 MB, 2143813632 bytes
2 heads, 63 sectors/track, 33231 cylinders, total 4187136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     4,187,135     4,187,104   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9166e76d-64a5-4ca3-b4ce-439628707d2a   ext3       320GB                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b92cf0ff-7776-476e-a531-a073d8fbf468   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        17b48cc8-3666-4e34-ab28-09d51354b6a4   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        455c84a2-4f62-4761-bde6-7ff38fff7011   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        E0FC-05DA                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw)
/dev/sda1        /media/320GB             ext3       (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9166e76d-64a5-4ca3-b4ce-439628707d2a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        9166e76d-64a5-4ca3-b4ce-439628707d2a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 8.04, kernel 2.6.24-16-rt (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-16-rt root=UUID=a86621ea-46eb-4d2b-b5d5-5935c69afff2 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode) (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-16-rt root=UUID=a86621ea-46eb-4d2b-b5d5-5935c69afff2 ro single 
initrd        /boot/initrd.img-2.6.24-16-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=a86621ea-46eb-4d2b-b5d5-5935c69afff2 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=a86621ea-46eb-4d2b-b5d5-5935c69afff2 ro single 
initrd        /boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title        Ubuntu 8.04, memtest86+ (on /dev/sdc1)
root        (hd2,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b92cf0ff-7776-476e-a531-a073d8fbf468 none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=c4760d20-1138-44fb-a401-5b0dd5dfda6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  52.6GB: boot/grub/menu.lst
  52.6GB: boot/grub/stage2
  52.6GB: boot/initrd.img-2.6.27-7-generic
  52.5GB: boot/initrd.img-2.6.28-11-generic
  52.6GB: boot/initrd.img-2.6.28-19-generic
  52.5GB: boot/initrd.img-2.6.28-3-rt
  52.5GB: boot/vmlinuz-2.6.27-7-generic
  52.5GB: boot/vmlinuz-2.6.28-11-generic
  52.6GB: boot/vmlinuz-2.6.28-19-generic
  52.5GB: boot/vmlinuz-2.6.28-3-rt
  52.6GB: initrd.img
  52.5GB: initrd.img.old
  52.6GB: vmlinuz
  52.5GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="2"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.36-1-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux    /boot/vmlinuz-2.6.36-1-lowlatency root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.36-1-lowlatency
}
menuentry 'Ubuntu, with Linux 2.6.36-1-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    echo    'Loading Linux 2.6.36-1-lowlatency ...'
    linux    /boot/vmlinuz-2.6.36-1-lowlatency root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.36-1-lowlatency
}
menuentry 'Ubuntu, with Linux 2.6.35-020635rc1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux    /boot/vmlinuz-2.6.35-020635rc1-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.35-020635rc1-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-020635rc1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    echo    'Loading Linux 2.6.35-020635rc1-generic ...'
    linux    /boot/vmlinuz-2.6.35-020635rc1-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-020635rc1-generic
}
menuentry 'Ubuntu, with Linux 2.6.33-29-realtime' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux    /boot/vmlinuz-2.6.33-29-realtime root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.33-29-realtime
}
menuentry 'Ubuntu, with Linux 2.6.33-29-realtime (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    echo    'Loading Linux 2.6.33-29-realtime ...'
    linux    /boot/vmlinuz-2.6.33-29-realtime root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.33-29-realtime
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro  splash vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 ro single  splash vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 17b48cc8-3666-4e34-ab28-09d51354b6a4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-19-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.28-19-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro single
    initrd /boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-3-rt (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro single
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu 9.04, kernel 2.6.27-7-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro quiet splash
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a ro single
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9166e76d-64a5-4ca3-b4ce-439628707d2a
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

#/dev/sr0 /media/cdrom0 udf,iso9660 defaults 0 0
UUID=9166e76d-64a5-4ca3-b4ce-439628707d2a /media/320GB ext3 defaults 0 1
UUID=17b48cc8-3666-4e34-ab28-09d51354b6a4 / ext4 defaults 0 1
UUID=b92cf0ff-7776-476e-a531-a073d8fbf468 swap swap sw 0 0
UUID=455c84a2-4f62-4761-bde6-7ff38fff7011 swap swap sw 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  66.7GB: boot/grub/core.img
 125.3GB: boot/grub/grub.cfg
  66.7GB: boot/initrd.img-2.6.32-21-generic
  66.8GB: boot/initrd.img-2.6.32-24-generic
 404.4GB: boot/initrd.img-2.6.33-29-realtime
 441.7GB: boot/initrd.img-2.6.35-020635rc1-generic
 437.1GB: boot/initrd.img-2.6.36-1-lowlatency
  66.7GB: boot/vmlinuz-2.6.32-21-generic
  66.7GB: boot/vmlinuz-2.6.32-24-generic
  66.8GB: boot/vmlinuz-2.6.33-29-realtime
  66.9GB: boot/vmlinuz-2.6.35-020635rc1-generic
  66.9GB: boot/vmlinuz-2.6.36-1-lowlatency
 437.1GB: initrd.img
 441.7GB: initrd.img.old
  66.9GB: vmlinuz
  66.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by lidex on 2011-05-08
Did you try the reset procedure from above? Try it again, exactly as written then immediately run:
```
lsusb
```

It looks like you're using a kernel from maverick. What is the reason for that
and have you tried reverting to lucid kernel?

---

### Post by BcRich on 2011-05-08
hi lidex
yea i tried the reset procedure, it seems to work on the omega just as it's been described but it had no effect on getting ubuntu to recognize the sound card again. 
lsusb still does no show the omega after running the reset procedure
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1210:0002  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 12d1:1464 Huawei Technologies Co., Ltd. 
Bus 001 Device 007: ID 1e3d:2095  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
this line Bus 002 Device 003: ID 1210:0002  and this line Bus 001 Device 007: ID 1e3d:2095  have no names attached to them, do you think that maybe ubuntu realizes something is plugged in there but it just doesn't know what? ...like maybe my sound card? (i don't know enough about linux, unfortunately).
> It looks like you're using a kernel from maverick. What is the reason for that
and have you tried reverting to lucid kernel? 	
the default kernel that came with 10.04 was making my cd drive usage unreliable, this upgrading to the kernel i'm currently using solved the problem and also fixed issues i was having with my mobile internet connection.
i have been using this kernel for some time and my sound was working on 10.04 even when i was using the upgraded kernel.
the sound only stopped working when i was trying to make my lexicon omega my default sound card out of three others on this computer. 
i didn't think that switching the order of sound cards would be such a technical issue :( thanks for your input, i appreciate your help.

---

### Post by lidex on 2011-05-08
I could see one of those being your device. There is also this in dmesg:
```
[    7.493379] snd_usb_audio: `' invalid for parameter `index'
```
When you tried to change the default, did you change or add a .conf file or asound.rc somewhere?

Try this in terminal:
```
sudo rmmod snd-usb-audio
```
```
sudo modprobe snd-usb-audio
```
Now:
```
aplay -l
```

---

### Post by Yellow Pasque on 2011-05-09
Try this to update the USB ID database. It won't make the card work, but at least it might  show the name in lsusb:
```
sudo update-usbids
```

---

### Post by BcRich on 2011-05-09
hi lidex
> When you tried to change the default, did you change or add a .conf file or asound.rc somewhere?
yes i modified alsa-base.conf. I listed the contents of the file in a previous post on this thread.
running
```
sudo rmmod snd-usb-audio
```
results in 
```
ERROR: Module snd_usb_audio does not exist in /proc/modules
```
sudo modprobe snd-usb-audio results in 

```
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.save line 2: ignoring bad line starting with 'options'
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.35-020635rc1-generic/kernel/sound/modules/snd-usb-audio.ko): Invalid argument
```
aplay -l
results in 
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```
hi Temüjin
running 
sudo update-usbids results in what appears to be a problem with connecting to the server, although my internet connection is fine. I use a usb huawei mobile device. here's the results of the command
```
--2011-05-09 21:21:12--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org... 208.73.210.155
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:21--  (try: 2)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:24--  (try: 3)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:28--  (try: 4)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:33--  (try: 5)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:39--  (try: 6)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:46--  (try: 7)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:21:54--  (try: 8)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:22:04--  (try: 9)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:22:14--  (try:10)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:22:25--  (try:11)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:22:36--  (try:12)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:22:47--  (try:13)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:22:58--  (try:14)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:23:09--  (try:15)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:23:20--  (try:16)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:23:31--  (try:17)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:23:44--  (try:18)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:24:00--  (try:19)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

--2011-05-09 21:24:11--  (try:20)  http://www.linux-usb.org/usb.ids
Connecting to www.linux-usb.org|208.73.210.155|:80... connected.
HTTP request sent, awaiting response... No data received.
Giving up.

update-usbids: download failed

```
Thank you both very much for your help! i am truly grateful.

---

### Post by lidex on 2011-05-10
Post these outputs please:
```
ls /etc/modprobe.d/
```
```
cat /etc/modprobe.d/alsa-base.conf
```

I also found these links:
[http://ubuntuforums.org/showthread.php?t=935679](http://ubuntuforums.org/showthread.php?t=935679)
[http://ardour.org/node/4064](http://ardour.org/node/4064)

---

### Post by BcRich on 2011-05-10
hi lidex
```
ls /etc/modprobe.d/
``````
alsa-base.conf              blacklist-oss.conf
alsa-base.save              blacklist-vmc.conf
blacklist-ath_pci.conf      blacklist-watchdog.conf
blacklist.conf              libpisock9.conf
blacklist-firewire.conf     nvidia-graphics-drivers.conf
blacklist-framebuffer.conf  oss-compat.conf
blacklist-modem.conf

```cat /etc/modprobe.d/alsa-base.conf
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd_usb_audio
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
#options snd-usb-audio index=-2
options snd-usb-us122l index=-2
#options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```I hope there's something in there, I'll have a look at those two links thanks for posting them :)

i checked out the links the first one is a bit old and it seems to imply that there is some sort of issue with the lexicon, but i don't think there is a problem with mine because if i boot into a 10.04 live CD my sound works fine through the lexicon omega. if i was to copy alsa-base.conf  from the live CD to replace it in my installation, would this be a bad idea?

---

### Post by lidex on 2011-05-10
OK. I want you to remove that alsa-base.save file:
```
sudo rm /etc/modprobe.d/alsa-base.save

```
**Reboot**

So if it works on LiveCD, run lsusb and alsa-info there so we can see the difference

---

