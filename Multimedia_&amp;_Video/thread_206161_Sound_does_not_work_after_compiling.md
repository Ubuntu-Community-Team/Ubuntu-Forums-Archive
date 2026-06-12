---
title: "Sound does not work after compiling"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by Absurd on 2006-06-29
I followed [this](http://ubuntuforums.org/showthread.php?t=205449) because I didn't have any sound. 

I found out that my onboard sound was ICH7. However, even after following all of the instructions to build the [drivers from the alsa-project](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel), and I type "sudo modprobe snd-" into the terminal I get "FATAL: Module snd_ not found."

Did I miss something?:confused:

---

### Post by Absurd on 2006-06-30
bump

well, I used the command "modinfo snd-hda-intel" and I get the following

```
filename:       /lib/modules/2.6.15-25-386/kernel/sound/pci/hda/snd-hda-intel.ko
license:        GPL
description:    Intel HDA driver
vermagic:       2.6.15-25-386 preempt 486 gcc-4.0
depends:        snd-pcm,snd-page-alloc,snd-hda-codec,snd,snd
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
srcversion:     CFC483BC3D9CEEF6D205B9A
parm:           enable:bool
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           model:Use the given board model. (charp)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           index:Index value for Intel HD audio interface. (int)
```

I even added "snd-hda-intel" to /etc/modules. However, when I use the command "aplay" I get 

```
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2148:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:548: audio open error: No such device
```

my /modprobe.d/alsa-base is

```
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
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0
```

cat /proc/asound/cards ouputs
```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 169
```

Typing "sudo modprobe snd-hda-intel" and pressing "TAB" twice doesn't show "snd-hda-intel" anywhere.

The alsamixer works fine (alsaconfig was even able to find the soundcard).

I just know I'm so close to finally achieving sound support, but I just need to know what I should do from here?

I do have the onboard sound enabled in the BIOS btw.

[edit]nm, I got it to work after doing

```
sudo gedit /etc/group
```

and adding my username to ```
audio:x:29:
```

---

