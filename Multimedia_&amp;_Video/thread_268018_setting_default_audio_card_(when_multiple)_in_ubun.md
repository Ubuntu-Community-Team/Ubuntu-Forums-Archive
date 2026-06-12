---
title: "setting default audio card (when multiple) in ubuntu"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by girasko_aei_didaskomenos on 2006-09-29
I have set up an ubuntu dapper and I have added an external usb audio card 
0 snd_intel8x0
1 snd_usb_audio

onboard:ICH6
usb:    UA25

the problem is that after following all the how-to forums I didn't manage to set the usb audio card as default. (the system->preferences->sounds does not have ANY effect).

*the command "asoundconf set-default-card UA25" did not work

*Changing my alsa-base file I managed to have a very funny situation where my midi files come out from the onboard card and the mp3 files from the usb  one!!! Now my file looks like:
# autoloader aliases
install sound-slot-0 modprobe snd_usb_audio
install sound-slot-1 modprobe snd_intel8x0

#install sound-slot-0 modprobe snd-card-0
#install sound-slot-1 modprobe snd-card-1
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

#gia na doume 
options snd_usb_audio index=1
options snd_intel8x0 index=0

options snd-usb-audio index=-2

Can you suggest anything or any other thread?

Cheers,
D.

---

### Post by pseudonym on 2006-09-29
Shouldn't you remove this line - options snd-usb-audio index=-2 ? The fact that the usb device is listed twice could be causing you problems. Also, although don't quote me on this, I think you have underscores where dashes should be - snd_usb_audio instead of snd-usb-audio .

---

### Post by girasko_aei_didaskomenos on 2006-09-29
I deleted the last line and nothing changed....

---

### Post by girasko_aei_didaskomenos on 2006-09-29
actually something very surreal happens, mp3 and audio plays through the usb card and midi (with timidity) plays only through the onboard audio card

---

### Post by pseudonym on 2006-09-29
Sorry, after editing alsa-base you should run - ```
sudo update-modules
sudo /etc/init.d/alsa-utils restart
``` if you haven't done so already...

---

### Post by girasko_aei_didaskomenos on 2006-10-02
no, it doesn't work.The system does whatever it wants!
No matter which card I set as default, it starts up with one of them (onboard or USB) and plays some file types (either midi,either mp3,either whetever!)
Any ideas?!

---

