---
title: "Laptop speakers not turning off when I use headphone socket"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by aberadam on 2008-03-10
I've tried messing around in alsamixer, no option to turn on jack sense.  

Tried adding options 'snd-hda-intel model=laptop' in '/etc/modprobe.d/alsa-base'

Get this in amixer controls: 

> umid=3,iface=MIXER,name='Headphone Playback Switch'
numid=17,iface=MIXER,name='PCM Playback Volume'
numid=7,iface=MIXER,name='Front Mic Boost'
numid=9,iface=MIXER,name='Front Mic Playback Switch'
numid=8,iface=MIXER,name='Front Mic Playback Volume'
numid=2,iface=MIXER,name='Front Playback Switch'
numid=1,iface=MIXER,name='Front Playback Volume'
numid=11,iface=MIXER,name='CD Playback Switch'
numid=10,iface=MIXER,name='CD Playback Volume'
numid=4,iface=MIXER,name='Mic Boost'
numid=6,iface=MIXER,name='Mic Playback Switch'
numid=5,iface=MIXER,name='Mic Playback Volume'
numid=13,iface=MIXER,name='Capture Switch'
numid=12,iface=MIXER,name='Capture Volume'
numid=16,iface=MIXER,name='Caller ID Switch'
numid=14,iface=MIXER,name='Input Source'
numid=15,iface=MIXER,name='Off-hook Switch'


Card: HDA Intel                                                             
Chip: Realtek ALC861-VD 

Any ideas on how to fix this?

---

### Post by aberadam on 2008-03-10
Here's /etc/modprobe.d/alsa-base for what it's worth:

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --q$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe$
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --q$
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modp$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

 Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq$
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
options snd-hda-intel single_cmd=1 model=lenovo
options snd-hda-intel model=laptop

---

### Post by aberadam on 2008-03-11
Bumpy.

---

### Post by snlzkn on 2008-07-19
I am also unable to solve this problem. Just for this issue I have to open my Vista :( Since I have to use my headphones. I tried changing alsa-base file but that didn't solve it either.
I have Asus M50Sa.

---

