---
title: "Sound Issue -- &quot;Popping&quot;"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Bonit27 on 2009-04-01
Hello,

After messing around with various streams in the volume control (in an attempt to get my laptop's built-in microphone working) I have caused my sound card to accompany all sounds with a loud, repetitive, "popping". This happens both from the speakers and headphones.

I have tried getting a fresh ALSA driver as per the sticky, no luck. Muting all other streams (but the master, PCM, and headphones/front) didn't do a thing either. 

I'm using an Acer EX5420 laptop with 8.04LTS, 32-bit. Any help would be appreciated, right now my speakers are next to useless!

Jon

---

### Post by jonnyg01 on 2009-11-30
same problem...random "pop"

---

### Post by jacobs444 on 2009-11-30
sorry to divert topic, but is this limited only to laptops? I have not, and hope not to experience this problem. using intel HD audio out

---

### Post by whoop on 2009-11-30
Could be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)

If it is, there is a (temporary) workaround for this problem (read the bug report)...

---

### Post by jonnyg01 on 2009-11-30
i don't know if it's laptop related. my computer was built but i do have an intel core 2 duo mobile processor...

Whoop,
i can follow the process to a point...
can you inform me on what exactly to enter in the terminal? I'm still getting to know the command line process.

---

### Post by whoop on 2009-11-30
> **jonnyg01 said:**
> i don't know if it's laptop related. my computer was built but i do have an intel core 2 duo mobile processor...

Whoop,
i can follow the process to a point...
can you inform me on what exactly to enter in the terminal? I'm still getting to know the command line process.

```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```

And comment out options snd-hda-intel power_save=10, via adding a # sign in front of it.
Save it, and (probably) reboot...

---

### Post by jonnyg01 on 2009-11-30
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

### Post by whoop on 2009-11-30
> **jonnyg01 said:**
> 
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

(last line should be changed to) look like:
> 
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N


---

### Post by jonnyg01 on 2009-11-30
I don't know how to change the name...
I understand what needs to be done. I need to know how to do it.  step by step, what to type.

---

### Post by whoop on 2009-11-30
> **jonnyg01 said:**
> I don't know how to change the name...
I understand what needs to be done. I need to know how to do it.  step by step, what to type.

Ehrr, well, once again:

Type
```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```
in the terminal. 
You should now have the application gedit containing the contents of /etc/modprobe.d/alsa-base.conf

The last line in gedit looks like:
> 
options snd-hda-intel power_save=10 power_save_controller=N

Add a # sign (Shift+3) at the beginning of this line (in the application Gedit) so that it looks like:
> 
#options snd-hda-intel power_save=10 power_save_controller=N


Click the Save button of gedit and close gedit, then restart your computer...

---

### Post by jonnyg01 on 2009-11-30
wow im sorry, i didnt realize the changes took place in the gedit. i feel stupid

---

### Post by whoop on 2009-11-30
> **jonnyg01 said:**
> wow im sorry, i didnt realize the changes took place in the gedit. i feel stupid

Hehehe, no worries...

---

