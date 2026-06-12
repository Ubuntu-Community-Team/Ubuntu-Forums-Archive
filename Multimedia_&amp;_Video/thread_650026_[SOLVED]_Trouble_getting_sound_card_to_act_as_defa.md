---
title: "[SOLVED] Trouble getting sound card to act as default"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by cipher_nemo on 2007-12-25
I hope someone will be able to help.

I'm trying to get my sound card to be the default selection for a remote to control the volume. Currently, the remote (using ati_remote2 module) is mapping to control the built-in sound chip volume level, which is disabled in the BIOS. The built-in sound chip is on an Intel ICH5 as an AC97 device (aka: Realtek). The sound card I have is a Creative Labs Audigy 4.

How do I disable any and everything related to the built-in sound card that is picked up via ALSA when it was once enabled. Here's my alsa-base file. I commented out the install sound-slots listings and added the one manually for snd_ca0106 to troubleshoot, which is my sound card (reported from less /proc/asound/modules).

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd_ca0106
#install sound-slot-0 /sbin/modprobe snd-card-0
#install sound-slot-1 /sbin/modprobe snd-card-1
#install sound-slot-2 /sbin/modprobe snd-card-2
#install sound-slot-3 /sbin/modprobe snd-card-3
#install sound-slot-4 /sbin/modprobe snd-card-4
#install sound-slot-5 /sbin/modprobe snd-card-5
#install sound-slot-6 /sbin/modprobe snd-card-6
#install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0

options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

---

### Post by cor2y on 2007-12-25
i don't know if that creative card is compatible yet but heres how you set a default sound card in Ubuntu.
Fire up the terminal and type
```

asoundconf list

```
to get your listing of audio devices, i don't know what list you will get printed out but heres mine
```

Names of available sound cards:
nForce2
Bt878
AV710

```
Nforce2  is my onboard sound card
AV710 is the Chaintech  AV-710 in my PCI slot
Bt878 is the audio inputs on the TV capture card that i have in another PCI slot.
To switch say from the Nforce2 on board audio to the Chaintech Card simply type in the terminal.
```

asoundconf set-default-card AV710
```
Then restart if the system doesn't stick with the card you selected simply add sudo in front of asoundconf. 
And thats it for choosing from a bunch of multiple sound devices.
In theory the selecting a new device via the alsa control panel ( alsa mixer) should work but i never got it to work myself.

---

### Post by cipher_nemo on 2007-12-26
Thanks cor2y! Awesome... that did the trick. :)

I also had another issue with sound (it was knocked out after attaching a USB Linksys wireless adapter), but I resolved that one thanks to the community docs' [sound troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshooting"). Major kudos to the people who helped with that guide as well.

Thanks again! I'm marking this as solved.

---

