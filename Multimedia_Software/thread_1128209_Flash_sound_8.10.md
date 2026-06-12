---
title: "Flash sound 8.10"
date: 2009-04-17
forum: Multimedia Software
---

### Post by Bigfootmech on 2009-04-17
I have a built in 5.1 soundcard, but I don't want to use it. Instead I have a pair of USB headphones I've plugged in. 

I've gone to System>Preferences>Sound and tested that the headphones work, and changed all the options to that one - and it does play stuff normally once it's downloaded even FLVs. 

Then on Youtube, it still tries to play through the built in card (big speakers - plus the sound is pretty shoddy) as opposed to the headphones.

Am I doing anything wrong? PS: Flash 10 is installed.

---

### Post by Bigfootmech on 2009-04-18
Bump and the same goes for all video streaming sites.

---

### Post by Bigfootmech on 2009-04-19
Can somebody please just reply? Even a mod saying "you posted it in the wrong forum".

---

### Post by Bigfootmech on 2009-04-19
Ok so apparently System>Preferences>Sound controls Gnome volume control which just ignores what ALSA defaults are, however firefox only responds to ALSA... I've tried looking at /etc/modprobe.d/alsa-base but fiddling with the devices doesn't seem to have any sort of impact...

PS: Running Ubuntu 8.10 (bootable CD) - so I can't restart after saving something. This is becasue my HDD is fried (usually this time of day I'm playing COD4 on windows XP so all of this is a bit new to me).

---

### Post by Bigfootmech on 2009-04-19
Well I FINALLY got it working.

Thanks for all your guys support and googles dedicated efforts at helping me for hours on end.

Here's the code I 'compiled' that I'll run from my USB stick from now on at boot (it works now, I don't care how, it just does).

If it helps anybody I'll be happy.

```
sudo rm -r /etc/modprobe.d/alsa-base
echo "
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1  && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx  && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134  && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd_intel8x0 index=-2
options snd_hda_intel index=-2
#options snd-usb-audio index=1
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
" | sudo tee -a /etc/modprobe.d/alsa-base
sudo killall pulseaudio
sudo alsa force-reload
cat /proc/asound/modules

```

---

