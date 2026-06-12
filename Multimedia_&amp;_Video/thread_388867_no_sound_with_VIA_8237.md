---
title: "no sound with VIA 8237"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by twidget on 2007-03-20
hi im trying to get the onboard sound working on a motherboard someone gave me.the sound chip appears to be a  VIA 8237.when i was originaly installing kubuntu i tried edgy but kept getting a sound server crash message every 5 minutes or so. now i have dapper on here and while i get no crash messages i also get no sound. heres my terminal output:

```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8                  237 AC97 Audio Controller (rev 60)


arcangel@vid2:~$ lsmod | grep -i snd
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_mpu401              6728  0
snd_via82xx            28824  3
gameport               15496  2 analog,snd_via82xx
snd_ac97_codec         93216  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  2 snd_mpu401,snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  17 snd_seq_oss,snd_seq,snd_mpu401,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd

arcangel@vid2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

ive twidled with alsamixer and  kmix but that didnt do anything.has anyone actualy gotten one of these things to work?if theres no way of making it work can anyone recomend a linux compatible sound card with surround sound and under say $30

---

### Post by twidget on 2007-03-20
heres my alsa-base i unfortunately have no idea what im looking at here. can anyone tell me if this is set up right?
```

arcangel@vid2:~$ sudo nano /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```

ive also tried these tutorials:
[http://ubuntuforums.org/showthread.php?t=289388&highlight=via+82xx+sound](http://ubuntuforums.org/showthread.php?t=289388&highlight=via+82xx+sound)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by electronikjunkie on 2007-03-20
try putting this at the bottom of "/etc/modprobe.d/aliases" and reboot.
```

alias snd-card-0 snd-via82xx
options snd-via82xx index=0

```

---

### Post by twidget on 2007-03-20
thanks for the reply but i actualy got it working just now. i will give my method in step by step format:
1)after hours of tinkering and reading posts track down the motherboard manual
2) read through it and discover this little gem: "to enable front panel audio remove jumpers between 9 and 10 and 5 and 6.
3)take  apart the computer.
4) jumpers missing. 
5)d'oh!! 
6)scrabble through old computer junk box. find last 2 jumpers.
7) insert first jumper.
8) lose second jumper.`
9) find second jumper. insert. 
10)re-assemble frankenputer.
11) boot. wait with bated breath as kde loads.
12) hear happy kde welcome noise.
13)do happy dance. 
14)feel dumb
.....i suppose the moral of the story is check your hardware. sorry about the trouble guys.

---

### Post by Erlander on 2007-03-21
Thank you for that.  I gave up trying to get my VIA 8237 sound working and was convinced it was faulty.  Have been running an extra sound card instead.  I just looked and yes the jumpers are off because I removed the for a different pc the motherboard was in because it had front panel audio.

Will try removing the pci sound card and putting the jumpers back later.

Thank you.

Rob

---

### Post by turntayble on 2007-06-03
Twidget, 

You were right!  I pulled an old Biostar P4VMA-M motherboard off my shelf which uses the v8237 chip and wasn't able to get sound.  After checking the manual and replacing the line out jumpers (5-6 and 9-10), sound works perfectly!!

---

