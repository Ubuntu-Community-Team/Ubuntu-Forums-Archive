---
title: "No Sound (Medion Akoya P416 MD 96688)"
date: 2009-05-11
forum: Multimedia Software
---

### Post by n00ki3 on 2009-05-11
Hi there ..
i'm new to Ubuntu and i need Sound.
I dont have any Sound on my Laptop :
This ist my Laptop
[IMG]http://ecx.images-amazon.com/images/I/41jvrOwtgyL._SL500_AA240_.jpg[/IMG]
i did this :

```

cat /proc/asound/cards 

```
```
-------------:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfb300000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfb010000 irq 17 

```
```
lspci | grep -i audio
```
```
--------------:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]

```
```

hwinfo --sound
```
```

--------------:~$ hwinfo --sound
09: PCI 100.1: 0403 Audio device                                
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1002_aa10
  Unique ID: NXNs.R8jFP8YJFAA
  Parent ID: vSkL.GplIvOMTy34
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "ATI RV610 audio device [Radeon HD 2400 PRO]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaa10 "RV610 audio device [Radeon HD 2400 PRO]"
  SubVendor: pci 0x161f "Rioworks"
  SubDevice: pci 0x206f 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfb010000-0xfb013fff (rw,non-prefetchable)
  IRQ: 17 (21 events)
  Module Alias: "pci:v00001002d0000AA10sv0000161Fsd0000206Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (PCI bridge)

23: PCI 1b.0: 0403 Audio device
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.x4OX_o3l_50
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801H (ICH8 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "82801H (ICH8 Family) HD Audio Controller"
  SubVendor: pci 0x161f "Rioworks"
  SubDevice: pci 0x206f 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfb300000-0xfb303fff (rw,non-prefetchable)
  IRQ: 22 (2489 events)
  Module Alias: "pci:v00008086d0000284Bsv0000161Fsd0000206Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
aus :)



```

So ... can anybody help me ?!
:confused:

---

### Post by andso on 2009-05-13
hi
problem here
[http://forum.ubuntu-fr.org/viewtopic.php?id=315718](http://forum.ubuntu-fr.org/viewtopic.php?id=315718)
a solution there ?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302145](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302145)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210865](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210865)

---

### Post by n00ki3 on 2009-07-21
either i am too dumb .. or it didn't worked :(

can someone help me ? :confused:

---

### Post by haiyun211 on 2009-07-21
What window manager are you using?

---

### Post by n00ki3 on 2009-07-21
I am using Gnome .

I think i know where the problem is .. 

but i have no solution .

head -n 1 /proc/asound/card0/codec*:
> Codec: SigmaTel ID 7698

see here :[http://www.google.de/search?hl=de&q=SigmaTel+ID+7698&btnG=Google-Suche&meta=&aq=f&oq=](http://www.google.de/search?hl=de&q=SigmaTel+ID+7698&btnG=Google-Suche&meta=&aq=f&oq=)

and i tried to patch it : 
[http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)

i didn't worked either.. 
what else can i try ?

---

### Post by igorzwx on 2009-07-21
lsmod | grep oss
lsmod | grep snd
QUOTE:
lsmod shows the kernel modules. 
the kernel modules of oss have oss in the name
the alsa kernel modules have snd in the name.

(as Martin explained)

---

### Post by n00ki3 on 2009-07-25
hi : 

lsmod | grep oss :
> 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer


lsmod | grep snd :
> 
snd_hda_intel         434356  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_timer              29704  1 snd_pcm
snd                    62628  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm



i can't unterstand the output :(

---

### Post by xc3RnbFO8P on 2009-07-25
Try:
> sudo apt-get install linux-backports-modules-generic
and restart the computer.

---

### Post by n00ki3 on 2009-07-25
couldn't find it :

> 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
E: Konnte Paket linux-backports-modules-generic nicht finden


edit : 
maybe i should try : 
linux-backports-modules-2.6.28-13-generic
or
linux-backports-modules-jaunty-generic
?

---

### Post by xc3RnbFO8P on 2009-07-26
Yes it should be:
> sudo apt-get install linux-backports-modules-jaunty-generic
and show the output of:
> gedit /etc/modprobe.d/alsa-base.conf

---

### Post by n00ki3 on 2009-07-26
alsa-base.conf:
> 
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=dell-d21


---

### Post by xc3RnbFO8P on 2009-07-26
First try this:
> sudo gedit /etc/modprobe.d/alsa-base.conf
add this line:
> options snd_hda_intel index=1,0
and restart the computer. 

> options snd-pcsp index=-2
options snd_hda_intel index=1,0
options snd-hda-intel model=dell-d21 

---

### Post by n00ki3 on 2009-07-26
no -- it doesn't work :(

---

### Post by xc3RnbFO8P on 2009-07-26
Change it again:
> options snd_hda_intel index=0,1 

---

