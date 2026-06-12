---
title: "No sound - Alsa blank window - Lucid  2.6.34 kernel"
date: 2010-09-04
forum: Multimedia Software
---

### Post by greylander on 2010-09-04
Hello,

I just updated the kernel to fix nvidia video problem.  But now I have problem of no sound.  I think it may be unrelated to the upgrade of kernel because most or all of the symptoms were already present, or the upgrade may have complicated things even more.  Another recent symptom in conjunction with this problem is that "restart" and "shutdown" from panel dropdown do not work -- they just log out.  May or may not be related at all.

Here is link to output of alsa-info.sh:

[http://www.alsa-project.org/db/?f=cca949e34cdc308c231c02568e17f882e01435d0](http://www.alsa-project.org/db/?f=cca949e34cdc308c231c02568e17f882e01435d0)

I saw this thread about upgrading alsa, but it seems to indicate that later than 2.6.32 kernel not supported (????): [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Here is my /etc/modprobe.d/alsa-base.conf.  The last line, "options snd-hda-intel model=basic" was from suggestions I found in other threads.

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
options snd-hda-intel model=basic
```

Here's hoping someone can help!!

---

### Post by greylander on 2010-09-04
Additional background info:

My sound has been working fine until today.  The problem started after a freeze which I believe was caused by clash between 2.6.32 kernel and Nvidia graphics drivers.  I have been have daily random freezes like this for a long time, but today after rebooting from freeze, there were strange problems with sound (alsmixer window blank, no volume control under speaker icon in task panel, and "restart" and "shutdown" from task panel not working [just logging out instead, apparently]).

In processing of attempting to fix problems, I upgraded kernel to 2.6.34, re-installed Nvidia drivers.  Not sure if this will fix the "freeze" problem (did this base on here:  [http://my.opera.com/linuxonlinehelp/blog/ubuntu-10-04-lucid-lynx-amd64-nvidia-195-current-freeze-hang-randomly](http://my.opera.com/linuxonlinehelp/blog/ubuntu-10-04-lucid-lynx-amd64-nvidia-195-current-freeze-hang-randomly) ) but it is encouraging, many glitchy graphics behaviors especially during boot up and shutdown have gone away.  

But the sound problem still remains.  The "restart" & "shutdown" problem also remains, but this thread is for the sound problem.  I mention the restart/shutdown only in case it is related.

I think in the last "freeze" something got corrupted, but I am not sure.

---

### Post by greylander on 2010-09-04
Maybe Solved!

I realized that I had not re-installed the alsa-base yet.  I had been re-installing the gnome-alsamixer.  (facepalm!)#-o

re-installing alsa-base appears to have repaired whatever was corrupted.  It also seems to have fixed the reboot/shutdown problem.

Before I mark this as "Solved" maybe someone knowledgeable can comment on what might have been going on and/or suggest if there are things I should check to verify that all is working properly?

Here is my latest alsa_info.sh:

[http://www.alsa-project.org/db/?f=d445dd0e74bfb8dd537c275324de8f2f54df323b](http://www.alsa-project.org/db/?f=d445dd0e74bfb8dd537c275324de8f2f54df323b)

---

### Post by lkjoel on 2010-09-10
> **greylander said:**
> Maybe Solved!

I realized that I had not re-installed the alsa-base yet.  I had been re-installing the gnome-alsamixer.  (facepalm!)#-o

re-installing alsa-base appears to have repaired whatever was corrupted.  It also seems to have fixed the reboot/shutdown problem.

Before I mark this as "Solved" maybe someone knowledgeable can comment on what might have been going on and/or suggest if there are things I should check to verify that all is working properly?

Here is my latest alsa_info.sh:

[http://www.alsa-project.org/db/?f=d445dd0e74bfb8dd537c275324de8f2f54df323b](http://www.alsa-project.org/db/?f=d445dd0e74bfb8dd537c275324de8f2f54df323b)
Do you have a working sound card?
If it still doesn't work, follow the Fix your sound! link in my signature.

---

### Post by greylander on 2010-09-10
Thanks.  Just motherboard sound.  It's all working.  It really does seem to have been something corrupted, and just re-installing the right thing" alsa-base, not alsamixer.

---

### Post by lkjoel on 2010-09-10
> **greylander said:**
> Thanks.  Just motherboard sound.  It's all working.  It really does seem to have been something corrupted, and just re-installing the right thing" alsa-base, not alsamixer.
Try the Fix your sound! link in my signature.
EDIT:
Ignore my comment, I just didn't read your post correctly!

---

