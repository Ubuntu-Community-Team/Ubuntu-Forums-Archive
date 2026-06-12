---
title: "Realtek ALC888 no sound at all"
date: 2009-11-10
forum: Multimedia Software
---

### Post by agalryunaer on 2009-11-10
Hi,

This is my first time posting here and this is the first time I install Ubuntu on this computer. It did not gave me any problem except with the sound card, since it does not play any sound under any application. 

However, I did ran alsamixer and found out the soundcard was a Realtek ALC888 on an Intel board.

I don't know to much about Linux, so I haven't tried any solution. I'll paste my alsa-base.conf in case it is needed.

Thank you so much for your time.

alsa-base.conf:


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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS &#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS &install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS &install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS &#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS &# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS &# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by agalryunaer on 2009-11-11
Any help with these? In the Spanish forum they told me to make the last line a comment, but it did not achieve anything. 
Any suggestions? 

Thanks,

---

### Post by mafitzpatrick on 2009-11-21
Hi. Did you get anywhere with this? I got the updates today and my audio suddenly stopped working, has been fine going back to 7.04. Same model/config as you have listed above.

I'm running Kubuntu, at startup I get an error that the soundcard is not detected (HDA Intel (ALC888 Analog)). Doing lspci gives:

Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

But I'm not convinced that's the actual soundcard, I'm sure it used to be listed as the line reported by Kubuntu.

Will keep looking, if anyone has any suggestions/reasons the update may have borked it I'm all ears :)

---

