---
title: "Problem With Soundblaster Audigy 1es"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by dimziou on 2007-06-11
I recently installed ubuntu 7.04 and everything works fine (thanks to ndiswrapper) but i can't get my sound card to work. It seems to be properly installed with the right module loaded, all channels are unmuted but no sound comes out. Below is the results from running commands **(aplay -l, lspci -v, sudo modprobe snd-)** and the contents of the **alsa-base **file   Please help... 

**dimziou@katevastiri:/etc/modprobe.d$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 ES [SB0160]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]  
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

card 0: Audigy [Audigy 1 ES [SB0160]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  
Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

card 0: Audigy [Audigy 1 ES [SB0160]], 
device 3: emu10k1 [Multichannel Playback]
  
Subdevices: 1/1
  Subdevice #0: subdevice #0


**dimziou@katevastiri:/etc/modprobe.d$ lspci -v**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: e6000000-e6ffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e000 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs Unknown device 0052
        Flags: bus master, medium devsel, latency 64, IRQ 12
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at e800 [size=8]
        Capabilities: <access denied>

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at ec00 [size=256]
        Memory at e8020000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e7000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Netgear Unknown device 6b00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        Memory at e8000000 (32-bit, non-prefetchable) [size=64K]
        Memory at e8010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04) (prog-if 00 [VGA])
        Subsystem: Diamond Multimedia Systems Viper V550
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e6000000 (32-bit, prefetchable) [size=16M]
        Expansion ROM at e5000000 [disabled] [size=64K]
        Capabilities: <access denied>



**dimziou@katevastiri:/etc/modprobe.d$ sudo modprobe snd-**
Display all 151 possibilities? (y or n)
snd-ac97-codec      snd-es1688          snd-opti93x
snd-ad1816a         snd-es1688-lib      snd-page-alloc
snd-ad1848          snd-es18xx          snd-pcm
snd-ad1848-lib      snd-es1938          snd-pcm-oss
snd-ad1889          snd-es1968          snd-pcxhr
snd-adlib           snd-es968           snd-pdaudiocf
snd-ainstr-fm       snd-fm801           snd-rawmidi
snd-ainstr-gf1      snd-gina20          snd-riptide
snd-ainstr-iw       snd-gina24          snd-rme32
snd-ainstr-simple   snd-gusclassic      snd-rme96
snd-ak4114          snd-gusextreme      snd-rme9652
snd-ak4117          snd-gus-lib         snd-rtctimer
snd-ak4531-codec    snd-gusmax          snd-sb16
snd-ak4xxx-adda     snd-gus-synth       snd-sb16-csp
snd-ali5451         snd-hda-codec       snd-sb16-dsp
snd-als100          snd-hda-intel       snd-sb8
snd-als300          snd-hdsp            snd-sb8-dsp
snd-als4000         snd-hdspm           snd-sbawe
snd-atiixp          snd-hwdep           snd-sb-common
snd-atiixp-modem    snd-i2c             snd-seq
snd-au8810          snd-ice1712         snd-seq-device
snd-au8820          snd-ice1724         snd-seq-dummy
snd-au8830          snd-ice17xx-ak4xxx  snd-seq-instr
snd-azt2320         snd-indigo          snd-seq-midi
snd-azt3328         snd-indigodj        snd-seq-midi-emul
snd-bt87x           snd-indigoio        snd-seq-midi-event
snd-bt-sco          snd-intel8x0        snd-seq-oss
snd-ca0106          snd-intel8x0m       snd-seq-virmidi
snd-cmi8330         snd-interwave       snd-serial-u16550
snd-cmipci          snd-interwave-stb   snd-sgalaxy
snd-cs4231          snd-korg1212        snd-sonicvibes
snd-cs4231-lib      snd-layla20         snd-sscape
snd-cs4232          snd-layla24         snd-tea575x-tuner
snd-cs4236          snd-maestro3        snd-tea6330t
snd-cs4236-lib      snd-mia             snd-timer
snd-cs4281          snd-miro            snd-trident
snd-cs46xx          snd-mixart          snd-trident-synth
snd-cs5535audio     snd-mixer-oss       snd-usb-audio
snd-cs8427          snd-mona            snd-usb-lib
snd-darla20         snd-mpu401          snd-usb-usx2y
snd-darla24         snd-mpu401-uart     snd-util-mem
snd-dt019x          snd-mtpav           snd-via82xx
snd-dummy           snd-mts64           snd-via82xx-modem
snd-echo3g          snd-nm256           snd-virmidi
snd-emu10k1         snd-opl3-lib        snd-vx222
snd-emu10k1-synth   snd-opl3sa2         snd-vx-lib
snd-emu10k1x        snd-opl3-synth      snd-vxpocket
snd-emu8000-synth   snd-opl4-lib        snd-wavefront
snd-emux-synth      snd-opl4-synth      snd-ymfpci
snd-ens1370         snd-opti92x-ad1848  
snd-ens1371         snd-opti92x-cs4231  

**dimziou@katevastiri:gedit alsa-base**
autoloader aliases
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

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by josesanders on 2007-06-11
A lot of people have been having problems with sound cards lately due to an issue with which one is considered the default.  Try this to specify the default card:

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

---

### Post by dimziou on 2007-06-12
I will try it tonight when i get home although i don't have an on board sound card.
Thanks and keep me in mind if you run across anything helpful.

---

### Post by josesanders on 2007-06-13
The reason that I suggested this for you is because of the saa7134.  I don't see it in your output from lspci, but I noticed that you load the saa7134 module.  I have one of those, and in my experience, it also is counted as a sound card.  I first experienced this problem because my system was sometimes counting the saa7134 as dsp0.

---

### Post by dimziou on 2007-06-16
Sorry for the delay, sometimes bosses can make you lose track of time, anyway i tried it and had no positive result so i will have to say that this is a bug(?) or that this is due to my inexperience with ubuntu and linux in general...
thanks and keep me in mind.
ps : maybe a clean installation can help?

---

