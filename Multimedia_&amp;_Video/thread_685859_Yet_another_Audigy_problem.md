---
title: "Yet another Audigy problem"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by Cereal_Killer on 2008-02-02
My problem is a little bit different than what I've found so far.  I have done an exhaustive search, but nothing that fits my problem.  I installed an Audigy SE card a few weeks ago, and every couple of startups it works fine, but after about 2 or 3 boots, it stops working.  I'll go through all the directions to get it working, nothing works.  Then the next time I boot up, it's working again.  Another boot, and it quits working again.  I'm at wits end with it.  I'm wanting to get completely away from Windoze XP, but this is one of the only things keeping from it.  Any help?

---

### Post by happyhamster on 2008-02-02
Did you disable onboard sound in the bios? If not, try that first.

If that doesn't work, could you show the output of the following commands:

aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base

They give detailed info about your sound hardware and configuration.

---

### Post by Cereal_Killer on 2008-02-02
Yes, I disabled the onboard audio in the bios.

aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards output:

 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xac00 irq 21
 1 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 17


cat /proc/asound/modules output:

 0 snd_ca0106
 1 snd_intel8x0

cat /etc/modprobe.d/alsa-base output:

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
options snd-C index=0
options snd-A index=1 options snd-B index=2


Right now the audio is working fine, except for the volume slider not working.  But at least I have audio.  But I'm pretty sure the next time I reboot it won't work.  Thanks for the help so far.

---

### Post by happyhamster on 2008-02-02
- If you don't use onboard sound, then the easiest way out is probably blacklisting the snd_intel8x0 module. In a terminal:

sudo nano /etc/modprobe.d/blacklist

- Add the following lines at the end of that file:

# Added by user, feb 2008
blacklist snd_intel8x0

- Save (ctrl-o) and exit the editor (ctrl-x). Next: reboot and check if the module is gone:

cat /proc/asound/modules

- Good luck, and keep us informed.



BTW, have you edited alsa-base before? I'm curious about the lines:

options snd-C index=0
options snd-A index=1 options snd-B index=2

Are they the result of a script perhaps? Did you have 3 soundcards at one time? (if you think I'm nosey, just say so :) )

---

### Post by Cereal_Killer on 2008-02-03
Well, I blacklisted that snd intel8x0 and rebooted.  It's working now, but I'm not sure how long.  Right after I wrote that last email, I shut down the computer, rebooted in the morning, and it worked fine.  Booted up again this morning, and nothing.  I blacklisted, rebooted and it seems to be working right now.  The volume slider is still not working, but at least I have sound.  I can deal with that right now, but would eventually like to get that fixed.  I never had 3 sound cards at the same time. 

Tried these "options snd-C index=0; options snd-A index=1 options snd-B index=2" but only got back "bash: options: command not found"

Owell, everything seems to be working for the moment.  Thanks a lot for the help.  We'll see if this holds for me.

---

### Post by happyhamster on 2008-02-03
Concerning the volume-slider: try right-clicking the volume-control icon. Choose the Preferences option. Below the selected device (probably some kind of alsa mixer) are all available sound channels (master, pcm, headphone, etc) The one you select in this menu is the channel changed by the volume-slider. Just keep trying till you find the one you want to use.

> **Cereal_Killer said:**
> Tried these "options snd-C index=0; options snd-A index=1 options snd-B index=2" but only got back "bash: options: command not found"
Those lines are already in you alsa-base configuration file. I just wondered how they got there, because they look a bit weird I think. No need to change them or such though. 

Anyway, keep us informed.

---

### Post by Cereal_Killer on 2008-02-03
Well, that's working now.  Tried it before and got nothing.  It turned out to be the Aux Front.  Very sensitive though.  Glad to have that working too.  Thanks a lot for the help.  I always knew Linux could do just about everything I wanted, and as good if not better than Windoze.

---

### Post by Michael Matthews on 2008-02-17
/proc/asound/modules looks WRONG!

Should be emu10k1
$ cat /proc/asound/modules
 0 snd_emu10k1
 1 snd_intel8x0

I would either re-install packages or rebuild alsa. Search audigy in forums for detailed instructions.

---

### Post by happyhamster on 2008-02-17
> **Michael Matthews said:**
> /proc/asound/modules looks WRONG!

Should be emu10k1
$ cat /proc/asound/modules
 0 snd_emu10k1
 1 snd_intel8x0

Are you sure about that? The audigy cards have a variety of soundchips and are supported by a few different drivers. According to this page:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

, an Audigy SE still uses the CA0106 module.

---

### Post by Cereal_Killer on 2008-02-17
Sorry for never writing back.  Mine's working perfectly fine now.  I think blacklisting the on-board sound did the trick.  And the volume controls show it's the CA0106.  No problems what-so-ever now.  Except for the keyboard volume controller doesn't control the main volume.  Which isn't too big of a deal t me, as I don't use it much anyway.

---

### Post by AmericanXer0 on 2008-02-21
> **happyhamster said:**
> - If you don't use onboard sound, then the easiest way out is probably blacklisting the snd_intel8x0 module. In a terminal:

sudo nano /etc/modprobe.d/blacklist

- Add the following lines at the end of that file:

# Added by user, feb 2008
blacklist snd_intel8x0

- Save (ctrl-o) and exit the editor (ctrl-x). Next: reboot and check if the module is gone:

cat /proc/asound/modules

- Good luck, and keep us informed.



I just came in here to say thanks, happyhamster. I was having the same problem with my Audigy 2 zs, and blacklisting my mobo sound caused my soundcard to start working again. 

Anybody else having a similar problem should try this out.

---

### Post by raashell on 2008-02-25
> **Michael Matthews said:**
> /proc/asound/modules looks WRONG!

Should be emu10k1
$ cat /proc/asound/modules
 0 snd_emu10k1
 1 snd_intel8x0

I would either re-install packages or rebuild alsa. Search audigy in forums for detailed instructions.

Michael,

 I came across something earlier today where someone was complaining because the Audigy ca0106 thingy (driver, device?) doesn't use emul10k1 like most (creative labs?) sound cards.  If it wasn't so buried in my history, I'd send a link.  Just wanted to comment that lacking emul10k1 may not be a problem.

John

---

