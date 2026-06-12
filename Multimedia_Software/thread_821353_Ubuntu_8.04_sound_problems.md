---
title: "Ubuntu 8.04 sound problems"
date: 2008-06-07
forum: Multimedia Software
---

### Post by anova on 2008-06-07
I have VGC-VA10G,
after install ubuntu 8.04 disappeared sound,
tried another kernel - without result,
driver tried Alsa
options [b]snd-hda-intel model = vaio
does not work
help, help where I was wrong!
VAIO only FOR WINDOWS?

---

### Post by Pjotr123 on 2008-06-07
I have a Sony Vaio myself, running fine on Ubuntu.

Check this how-to:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by ethanklein on 2008-06-07
I dont know if this has anything to do with it but if you installed using the Live CD I've heard can cause problems. I installed using the Live CD and my sound didnt work until I used the Alternate CD.

---

### Post by xc3RnbFO8P on 2008-06-07
You could try this:
> sudo gedit /etc/modprobe.d/alsa-base
replace  options snd-hda-intel model = vaio
with
options snd-hda-intel model=vaio position_fix=0

Restart the computer.

---

### Post by anova on 2008-06-20
> **Ringi said:**
> You could try this:

Restart the computer.

SUPER!!!!
Position fix 0 it really!!!!
ALL ITS WORK :)
:guitar:
THanks!!!!!

---

### Post by vanweezy on 2008-06-20
I tried the sudo gedit /etc/modprobe.d/alsa-base command and got returned this.

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
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

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
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

I am dual booting Ubuntu on a Sony Vaio VGC-RB52.  Any help in noobspeak would be much appreciated as I am about 3 days old in Ubuntu time.

---

### Post by agasamapetilon on 2008-06-21
You have to paste this line:
options snd-hda-intel model=vaio position_fix=0 into
 inside: 
# Prevent abnormal drivers from grabbing index 0: 
 and save the changes and restart your laptop. 

I hope this will work for you mate, I tried the same but didn't worked for me, as soon as I fix this I will update a bit more info.

---

### Post by anova on 2008-06-25
But sound only in headphones !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:(:(:(:

---

### Post by donut123 on 2011-02-28
I must be seeing things..I must have posted the other reply all the way  out in la la land..
Can any one tell me if someone found a solution to this issue/ 
Thank you

---

