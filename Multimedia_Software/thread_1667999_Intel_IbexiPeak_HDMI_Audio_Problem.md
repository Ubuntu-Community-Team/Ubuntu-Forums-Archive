---
title: "Intel IbexiPeak HDMI Audio Problem"
date: 2011-01-15
forum: Multimedia Software
---

### Post by Lukiwuki on 2011-01-15
Hi @ all

I've got an Acer PRO5IF Laptop.
Yesterday I installed Ubunu 10.10. Now I want to listen to the audio via some headphones.
The point is it does not work.
The normal sound works but there is no sound on my headphones. If I plug them in nothing happens an the sound is still playing over the normal laptop output.

I've tried to edit the /etc/modprobe.d/alsa-base.conf. I added > options snd-hda-intel mode=acerI tried to chenge the mode to "lenovo" and so on but still nothing happend after reloading alsa.

Additional information:
> head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20585

==> /proc/asound/card0/codec#3 <==
Codec: Intel IbexPeak HDMI> cat /proc/asound/cards  
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd5400000 irq 47
Im sorry for my english but can anyone please help me? I tried google but nothing worked.

Thanks

---

### Post by lidex on 2011-01-16
This is not an hdmi problem. Headphones are through an analog output. Try this and let me know the result. Fire up a terminal="Applications->Accessories->Terminal" and input this:
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Lukiwuki on 2011-01-16
No change. But thanks for trying to help me :)

Edit:

The results of:
> cat /etc(modprobe.d/alsa-base.conf> # autoloader aliases
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
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
# Eigene Konfiguration
options snd-hda-intel model=thinkpad


---

### Post by lidex on 2011-01-18
OK. Let's try this. Remove that file edit:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
and replace it with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes

```

---

### Post by klmpencran on 2011-01-19
Hi,

I'm following the resolution of this problem 'cause I've a HP ProBook 6540b on which I encountered a similar problem :

I installed a fresh Ubuntu 10.10 on it and everything worked fined till I decided to plug hearphones to listen to music during my working period, without disturbing my collegues. Since that, sound works only with the hearphones, no more sound with the notebook's speakers.

alsamixer reports an HDA Intel Card and an IbexPeak HDMI Chip.

I tried to edit alsa-base.conf which seems to be rather common on my laptop : no particular line for a specific chip detected. But nothing changed for me with the options above.

My french english is perhaps not as good as I would want so if you have any question, please let me know.

Bye.

---

### Post by Lukiwuki on 2011-01-19
Does not work for me either.
Now restored the old alsa-base.conf.
But thx for trying.

---

### Post by Lukiwuki on 2011-01-19
Does not work for me either.
But thanks  for trying.

---

### Post by Lukiwuki on 2011-01-19
Does not work for me either.
But thanks  for trying.

---

### Post by Lukiwuki on 2011-01-19
Does not work for me either.
But thanks  for trying to help.

---

### Post by Lukiwuki on 2011-01-19
Doesn't work for me either.
But thanks for trying.

---

### Post by Lukiwuki on 2011-01-19
Doesn't work for me either.
But thanks for trying.

---

### Post by Lukiwuki on 2011-01-19
Doesnt work for me either, but thanks for trying.

Sry for posting like 500 times but atm I'm online via HSDPA and my internet is some kind of buggy.

---

