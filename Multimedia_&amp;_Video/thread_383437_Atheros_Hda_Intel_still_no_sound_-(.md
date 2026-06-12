---
title: "Atheros Hda Intel: still no sound :-("
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by bracc0 on 2007-03-13
...and I still am a newbie :-)
I've read dozen of posts, I've re-read the fine document "Comprehensive Sound Problem Solutions Guide", I've upgraded alsa base (upg. to 1.0.13-5) and alsa utils (upg. to 1.0.13-2) to the newest release found in debian packages, I've muted/unmuted in any possible combination the columns in alsamixer, I've checked that my user has the rights to play sounds, I rebooted several times, I've checked in System-->Preferences-->Audio that ALSA is selected, but I still have no sound. I can't hear neither sounds nor system beep.
My laptop has dual boot Edgy/Window$ XP professional. Needless to say, with Window$ I can hear everything. 

Any help is greatly appreciated.

Here are some outputs:

output of lshw

```

lshw:

 *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:f0640000-f0643fff irq:74

```

output of lspci -v

```

lspci -v:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
        Subsystem: Fujitsu Limited. Unknown device 1397
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at f0640000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

``` 

output of aplay -l

```

aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

my /etc/modules contents:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ath-pci
snd-hda-intel

```

Contents of the file /etc/modprobe.d/alsa-base:

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7
# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /lib/alsa/modprobe-post-install snd-emu10k1 ; /sbin/modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /lib/alsa/modprobe-post-install snd-via82xx ; /sbin/modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth /sbin/modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth /sbin/modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a /sbin/modprobe --ignore-install snd-ad1816a $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 /sbin/modprobe --ignore-install snd-ad1848 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ad1848
install snd-adlib /sbin/modprobe --ignore-install snd-adlib $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-adlib
install snd-ad1889 /sbin/modprobe --ignore-install snd-ad1889 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ad1889
install snd-ali5451 /sbin/modprobe --ignore-install snd-ali5451 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 /sbin/modprobe --ignore-install snd-als100 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-als100
install snd-als300 /sbin/modprobe --ignore-install snd-als300 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-als300
install snd-als4000 /sbin/modprobe --ignore-install snd-als4000 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-als4000
install snd-aoa /sbin/modprobe --ignore-install snd-aoa $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa
install snd-aoa-fabric-layout /sbin/modprobe --ignore-install snd-aoa-fabric-layout $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa-fabric-layout
install snd-aoa-onyx /sbin/modprobe --ignore-install snd-aoa-onyx $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa-onyx
install snd-aoa-tas /sbin/modprobe --ignore-install snd-aoa-tas $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa-tas
install snd-aoa-toonie /sbin/modprobe --ignore-install snd-aoa-toonie $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa-toonie
install snd-aoa-soundbus /sbin/modprobe --ignore-install snd-aoa-soundbus $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa-soundbus
install snd-aoa-soundbus-i2s /sbin/modprobe --ignore-install snd-aoa-soundbus-i2s $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-aoa-soundbus-i2s
install snd-armaaci /sbin/modprobe --ignore-install snd-armaaci $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi /sbin/modprobe --ignore-install snd-asihpi $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp /sbin/modprobe --ignore-install snd-atiixp $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 /sbin/modprobe --ignore-install snd-au1x00 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 /sbin/modprobe --ignore-install snd-au8810 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 /sbin/modprobe --ignore-install snd-au8820 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 /sbin/modprobe --ignore-install snd-au8830 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 /sbin/modprobe --ignore-install snd-azt2320 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 /sbin/modprobe --ignore-install snd-azt3328 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 /sbin/modprobe --ignore-install snd-ca0106 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 /sbin/modprobe --ignore-install snd-cmi8330 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci /sbin/modprobe --ignore-install snd-cmipci $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 /sbin/modprobe --ignore-install snd-cs4231 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 /sbin/modprobe --ignore-install snd-cs4232 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 /sbin/modprobe --ignore-install snd-cs4236 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 /sbin/modprobe --ignore-install snd-cs4281 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx /sbin/modprobe --ignore-install snd-cs46xx $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-cs5535audio /sbin/modprobe --ignore-install snd-cs5535audio $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-cs5535audio
install snd-darla20 /sbin/modprobe --ignore-install snd-darla20 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 /sbin/modprobe --ignore-install snd-darla24 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x /sbin/modprobe --ignore-install snd-dt019x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g /sbin/modprobe --ignore-install snd-echo3g $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x /sbin/modprobe --ignore-install snd-emu10k1x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 /sbin/modprobe --ignore-install snd-ens1370 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 /sbin/modprobe --ignore-install snd-ens1371 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 /sbin/modprobe --ignore-install snd-es1688 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx /sbin/modprobe --ignore-install snd-es18xx $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 /sbin/modprobe --ignore-install snd-es1938 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 /sbin/modprobe --ignore-install snd-es1968 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 /sbin/modprobe --ignore-install snd-es968 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 /sbin/modprobe --ignore-install snd-fm801 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x /sbin/modprobe --ignore-install snd-fm801-tea575x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 /sbin/modprobe --ignore-install snd-gina20 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 /sbin/modprobe --ignore-install snd-gina24 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic /sbin/modprobe --ignore-install snd-gusclassic $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme /sbin/modprobe --ignore-install snd-gusextreme $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax /sbin/modprobe --ignore-install snd-gusmax $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony /sbin/modprobe --ignore-install snd-harmony $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp /sbin/modprobe --ignore-install snd-hdsp $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm /sbin/modprobe --ignore-install snd-hdspm $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 /sbin/modprobe --ignore-install snd-ice1712 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 /sbin/modprobe --ignore-install snd-ice1724 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo /sbin/modprobe --ignore-install snd-indigo $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj /sbin/modprobe --ignore-install snd-indigodj $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio /sbin/modprobe --ignore-install snd-indigoio $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 /sbin/modprobe --ignore-install snd-intel8x0 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave /sbin/modprobe --ignore-install snd-interwave $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb /sbin/modprobe --ignore-install snd-interwave-stb $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 /sbin/modprobe --ignore-install snd-korg1212 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 /sbin/modprobe --ignore-install snd-layla20 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 /sbin/modprobe --ignore-install snd-layla24 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 /sbin/modprobe --ignore-install snd-maestro3 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia /sbin/modprobe --ignore-install snd-mia $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mia
install snd-miro /sbin/modprobe --ignore-install snd-miro $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart /sbin/modprobe --ignore-install snd-mixart $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona /sbin/modprobe --ignore-install snd-mona $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 /sbin/modprobe --ignore-install snd-mpu401 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle /sbin/modprobe --ignore-install snd-msnd-pinnacle $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav /sbin/modprobe --ignore-install snd-mtpav $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mtpav
install snd-mts64 /sbin/modprobe --ignore-install snd-mts64 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-mts64
install snd-nm256 /sbin/modprobe --ignore-install snd-nm256 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 /sbin/modprobe --ignore-install snd-opl3sa2 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 /sbin/modprobe --ignore-install snd-opti92x-ad1848 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 /sbin/modprobe --ignore-install snd-opti92x-cs4231 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x /sbin/modprobe --ignore-install snd-opti93x $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 /sbin/modprobe --ignore-install snd-pc98-cs4232 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp /sbin/modprobe --ignore-install snd-pcsp $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr /sbin/modprobe --ignore-install snd-pcxhr $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf /sbin/modprobe --ignore-install snd-pdaudiocf $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus /sbin/modprobe --ignore-install snd-pdplus $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 /sbin/modprobe --ignore-install snd-portman2x4 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac /sbin/modprobe --ignore-install snd-powermac $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 /sbin/modprobe --ignore-install snd-pxa2xx-ac97 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-pxa2xx-i2sound /sbin/modprobe --ignore-install snd-pxa2xx-i2sound $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-pxa2xx-i2sound
install snd-riptide /sbin/modprobe --ignore-install snd-riptide $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-riptide
install snd-rme32 /sbin/modprobe --ignore-install snd-rme32 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 /sbin/modprobe --ignore-install snd-rme96 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 /sbin/modprobe --ignore-install snd-rme9652 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 /sbin/modprobe --ignore-install snd-s3c2410 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 /sbin/modprobe --ignore-install snd-sa11xx-uda1341 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 /sbin/modprobe --ignore-install snd-sb16 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 /sbin/modprobe --ignore-install snd-sb8 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe /sbin/modprobe --ignore-install snd-sbawe $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serial-u16550 /sbin/modprobe --ignore-install snd-serial-u16550 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy /sbin/modprobe --ignore-install snd-sgalaxy $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes /sbin/modprobe --ignore-install snd-sonicvibes $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape /sbin/modprobe --ignore-install snd-sscape $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 /sbin/modprobe --ignore-install snd-sun-amd7930 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 /sbin/modprobe --ignore-install snd-sun-cs4231 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri /sbin/modprobe --ignore-install snd-sun-dbri $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident /sbin/modprobe --ignore-install snd-trident $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio /sbin/modprobe --ignore-install snd-usb-audio $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y /sbin/modprobe --ignore-install snd-usb-usx2y $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 /sbin/modprobe --ignore-install snd-vx222 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxpocket /sbin/modprobe --ignore-install snd-vxpocket $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront /sbin/modprobe --ignore-install snd-wavefront $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci /sbin/modprobe --ignore-install snd-ymfpci $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel index=0
options snd-bt87x index=-2
options snd-cx88_alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

```

Anyone can help, please?
Thanks in advance
Claudio

---

### Post by bracc0 on 2007-03-14
Anyone can help, please?
Thank you in advance
Claudio

---

### Post by fNNR on 2007-03-14
I have almost the exact same problem. I'm also running a dual boot machine, and the sound works fine in Windows but it doesnt work in Ubuntu. I've red through several posts and nothing seems to help. 

Here are some of my outputs:

From aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

From lshw:

```

        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:ee400000-ee403fff irq:74


```

From lspci -v

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 2010
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>



```

I've checked the alsamixer and sound preferences and so on, but nothing seems to work so far. Any help is greatly appriciated!

---

### Post by herson on 2007-03-15
I have the same problem

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

I only run Ubuntu feisty in my toshiba laptop. Everything was ok with Ubuntu, kernel 2.6.20-8-generic, but when I update to Ubuntu, kernel 2.6.20-9-generic and Ubuntu, kernel 2.6.20-10-generic I only can hear sounds with a very (very) low volume... just a whisper... :(

---

### Post by Raein on 2007-03-16
hi, we all got the same problem with the snd-hda-intel sound. It has been 4 days since i install kubuntu in my sister laptop still i can't find the solution. I followed this help guide [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29) but no luck i still can't hear any sounds. I already install the stable and the development driver of alsa but no luck. I installed opensuse but the same problem that i encountered in kubuntu.

here is some of the configuration...

lshw
```

*-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:b0000000-b0003fff irq:11
```

lspci -v
```

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 3741
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/etc/modules

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2

```

/etc/modprobe.d/alsa-base
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel model=laptop
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

```

Please can anyone help us :( :( :(

---

### Post by bracc0 on 2007-03-19
> **Raein said:**
> 

Please can anyone help us :( :( :(

It seems that there is something mysterious that prevent our snd-hda-intel card to work.
I hope that in future versions of ubuntu it will be fixed.

Claudio

---

### Post by zeus77 on 2007-03-20
i've got the lenovo n100 with a broadcom wireless card... there are lots of suggestions for getting sound to work with Lenovos (search the forum), but the only one that worked for me was to add "acpi=ht" to the grub boot command...

---

### Post by eggdeng on 2007-03-21
A lot of the Intel HDA problems just require finding the right option to add in /etc/modprobe.d/alsa-base. Suggestions for different models at

[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by dunkgreen on 2007-03-21
I have a Acer Aspire 5050 which I've been trying to fix the sound on for weeks.  The simple fixed found here did the trick:  

[URL="http://www.nosredna.net/TikiWiki/tiki-view_blog.php?blogId=11"]
http://www.nosredna.net/TikiWiki/tiki-view_blog.php?blogId=11[/URL]

I hope it can help you too.

Bill D-G
Toronto ON

---

### Post by bobreeves on 2007-03-25
I went thru all the same things you did - spent many many days looking for a solution. The solution for me was switch to Parsix. Maybe I'll try Ubuntu again in a month or two.

---

