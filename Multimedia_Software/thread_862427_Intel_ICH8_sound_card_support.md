---
title: "Intel ICH8 sound card support"
date: 2008-07-17
forum: Multimedia Software
---

### Post by rolotomasee on 2008-07-17
Ok I've tried everything I can find to solve this problem. I know it's common enough with my sound card... Sound only out of headphone jack and only at low volume and very scratchy. Have tried playing with levels, alsamixer, etc. uninstalling/reinstalling ALSA, tried to switch to OSS, Pulse audio, tried installing backports, tried editing /etc/modprobe.de/alsa-base in a variety of ways, basically everything in the comprehensive sound guide, no luck.

I have an Acer aspire 6920 running a dual boot of vista (first) and ubuntu hardy heron 8.04. The sound card is detected, here is the output from "aplay -l":

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and the output from lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 0146
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


there is an interesting "access denied" there not sure what that's about...

---

### Post by odysseusjak on 2008-07-17
You could try:

[http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)

or

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by rolotomasee on 2008-07-17
Ok neither of those work and I had actually tried them before thanks for the suggestion though. Managed to update the alsa drivers as suggested in your first link that worked fine but made no difference.
The second link got stuck at installing the alsa driver. Got the following error messages for the "make" then "make install" commands...

Error when "making" alsa driver

rolotomasee@ScootyPuffSnr:~/alsa-driver-1.0.14$ sudo make
make dep
make[1]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore/ioctl32'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore/ioctl32'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore/oss'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore/oss'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore/seq'
make[4]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore/seq/instr'
make[4]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore/seq/instr'
make[4]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore/seq/oss'
make[4]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore/seq/oss'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore/seq'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/i2c'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/i2c/other'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/i2c/other'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/i2c'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/drivers'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/mpu401'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/mpu401'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/opl3'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/opl3'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/opl4'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/opl4'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/pcsp'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/pcsp'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/vx'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/drivers/vx'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/drivers'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/ad1816a'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/ad1816a'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/ad1848'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/ad1848'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/cs423x'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/cs423x'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/es1688'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/es1688'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/gus'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/gus'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/msnd'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/msnd'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/opti9xx'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/opti9xx'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/sb'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/sb'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/isa/wavefront'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa/wavefront'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/isa'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/synth'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/synth/emux'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/synth/emux'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/synth'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ac97'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ac97'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ali5451'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ali5451'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/asihpi'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/asihpi'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/au88x0'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/au88x0'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ca0106'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ca0106'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/cs46xx'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/cs46xx'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/echoaudio'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/echoaudio'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/emu10k1'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/emu10k1'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/hda'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/hda'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ice1712'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ice1712'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/korg1212'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/korg1212'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/mixart'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/mixart'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/nm256'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/nm256'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/pcxhr'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/pcxhr'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/pdplus'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/pdplus'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/riptide'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/riptide'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/rme9652'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/rme9652'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/trident'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/trident'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/vx222'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/vx222'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ymfpci'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci/ymfpci'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pci'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/aoa'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/codecs'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/codecs'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/core'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/core'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/fabrics'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/fabrics'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/soundbus'
make[4]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/aoa/soundbus'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/aoa'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/soc'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/soc/at91'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/soc/at91'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/soc/codecs'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/soc/codecs'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/soc/pxa'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/soc/pxa'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/soc/sh'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/soc/sh'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/soc'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/usb'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/usb/caiaq'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/usb/caiaq'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/usb/usx2y'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/usb/usx2y'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/usb'
make[2]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pcmcia'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/pcmcia/vx'
make[3]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pcmcia/vx'
make[2]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/pcmcia'
make[1]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14'
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/rolotomasee/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/rolotomasee/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
[COLOR="Red"]make[2]: *** [/home/rolotomasee/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/home/rolotomasee/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2
[/COLOR]



Error when make install alsa driver
rolotomasee@ScootyPuffSnr:~/alsa-driver-1.0.14$ sudo make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/rolotomasee/alsa-driver-1.0.14/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.24-19-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
make[1]: Entering directory `/home/rolotomasee/alsa-driver-1.0.14/acore'
mkdir -p /lib/modules/2.6.24-19-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.24-19-generic/kernel/sound/acore
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
[COLOR="Red"]make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/rolotomasee/alsa-driver-1.0.14/acore'
make: *** [install-modules] Error 1
[/COLOR]

---

