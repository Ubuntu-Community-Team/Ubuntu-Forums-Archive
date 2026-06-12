---
title: "FATAL: Module alsa not found [ATI SB450]"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by soundwave on 2007-11-21
Im in Gutsy 7.10 with kernel 2.6.22-14

with **lspci**, show soundcard:
```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
```

open ** alsamixer**:
```
soundwave@acer_abg:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
soundwave@acer_abg:~$ 

```

and file /etc/modprobe.d/alsa-base:

```
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

i am reinstall alsa (first purge, install)

can you guide me please ?

thanks

excuse me for my english

---

### Post by soundwave on 2007-11-22
any idea??

---

### Post by soundwave on 2007-11-23
:(

---

### Post by lazyrussian on 2007-11-23
I have the exact same problem, which is odd. This is my first reinstall of the OS on this laptop, and whatever I've done in the past (I found my old posts on here), don't work.

Recompiling the Alsa Drivers DOES NOT WORK :(

I've spent the last 3 hours reading and trying a lot of different methods, kind odd how two of us have this same problem within the last few days.

I'll keep tyring, and if I find anything, I'll post back.

---

### Post by soundwave on 2007-11-23
> **lazyrussian said:**
> This is my first reinstall of the OS on this laptop.

This is not WINDOWS, i will not reinstall, because i have sound in other kernel  ...i will discover the problem!

---

### Post by lazyrussian on 2007-11-23
No no, you're missing the point.

I've had ubuntu on here before.

I had edgy which also had sound problems, then I had feisty, and everything started to work, then when I upgraded again to gutsy, everythign worked the first time around.

For various reasons, I had to reinstall gutsy on my computer - a fresh install didnt work, but installing feisty and then gutsy on top of that did the trick - the only problem is that I can't get my sound to work now.

I used my old methods that I did when I was on edgy (I found my old posts, and maybe again on feisty - I think I didn't have problems, but not sure). The point is, those methods no longer work.

It's a completely different problem.

Anyway, need to reboot, just did a few things while I typed this up - hopefully something will work.

---

### Post by lazyrussian on 2007-11-23
Ok, the reboot + some of my tinkering fixed some stuff.

Still no sound, but my speaker-icon no longer has the red X next to it, and alsamixer now works.

Here's basically what I did:
Opened Synaptic and installed alsamixergui and reinstalled all the alsa packages that were in the generic install + a few more alsa common packages, can't remember the names.

I'll give you a full list once I get the sound back up.

---

### Post by soundwave on 2007-11-23
In console to run **lsmod | grep snd** the system* [actual kernel 2.6.22-14]* dont give me nothing, but if i do at previous kernel *[2.6.20-16, where i have sound]* the system give me the following:

```
soundwave@acer_abg:~$ lsmod | grep snd
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  2 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  2 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
soundwave@acer_abg:~$
```

what will be the problem... i believe be near to solution

a ubunter say me, what check the next packs in my system, and i have thats packs .... :??
[http://img440.imageshack.us/img440/9099/screenshot2cc6.png](http://img440.imageshack.us/img440/9099/screenshot2cc6.png)
[http://img440.imageshack.us/img440/5599/screenshot3fo3.png](http://img440.imageshack.us/img440/5599/screenshot3fo3.png)

---

### Post by lazyrussian on 2007-11-26
Alright, I got my sound to work.

I'll try to write up a HOWTO guide as soon as I can - quite busy for the next few days.

---

### Post by soundwave on 2007-11-26
Solution:
[I][B]
    sudo aptitude install module-assistant build-essential

    sudo module-assistant prepare,update

    sudo module-assistant build,install alsa

    sudo depmod
[/B][/I]

To reboot system, sound returns :D

thanks

PD: que wena onda ya tengo sonido!!! ...no cachan español ??? xDDDD

saludos de Chile

---

### Post by bayvista on 2007-12-23
Tried this Got:

Bad luck, the kernel headers for the target kernel version could   &#9618;     
     &#9474; not be found                                                       &#9618;     
     &#9474; and you did not specify other valid kernel headers to use

after the sudo module-assistant build,install alsa.

---

