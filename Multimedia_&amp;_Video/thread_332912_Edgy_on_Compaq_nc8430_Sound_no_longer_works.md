---
title: "Edgy on Compaq nc8430: Sound no longer works"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by DarthPlageus on 2007-01-06
After installing Edgy on my HP Compaq nc8430 laptop, the sound/audio no longer works.  It was working A-OK with Dapper.  I followed the directions in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to install the latest alsa drivers and such, but still no-go.  I have also followed advice provided in:

[http://www.ubuntuforums.org/showthread.php?p=1936060](http://www.ubuntuforums.org/showthread.php?p=1936060)
[http://www.ubuntuforums.org/showthread.php?t=235245](http://www.ubuntuforums.org/showthread.php?t=235245)

I did run alsamixer and have Master set to 100 and PCM set to 81.  One odd thing is that whenever I run RealPplayer, then quit it, then run alsamixer, it shows PCM back to 0.  Even though this does not happen with XMMS, there is still no sound.

Here is the sound info for my laptop, in case it helps:

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4700000 irq 177

$ cat /proc/asound/devices
  2:        : timer
  3: [ 0- 6]: digital audio playback
  4: [ 0- 6]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control


$  head -1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1981

==> /proc/asound/card0/codec#1 <==
Codec: Generic 11c1 Si3054


$  lspci -v |grep -A 5 Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a3
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at f4700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


$ cat /etc/modprobe.d/alsa-base
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# options snd-hda-intel model=3stack   <--- I did try this but no luck
options snd-hda-intel model=AD1981


--john

---

### Post by 8086ed on 2007-01-07
Try:

```
sudo apt-get install gnome-alsamixer
```

In the terminal, then run

```
gnome-alsamixer
```



Un-mute all of the channels.

This was suggested here:

[http://ubuntuforums.org/showthread.php?p=1978967#post1978967]("http://ubuntuforums.org/showthread.php?p=1978967#post1978967")

By wildcarde.

---

### Post by DarthPlageus on 2007-01-14
Thanks for the response.   I use XUbuntu, not the Ubuntu w/ Gnome.  However, I still ran alsamixer and unmuted ALL channels, rebooted, and still no-go.

Note that:

~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1.
Compiled on Jan  6 2007 for kernel 2.6.17-10-generic (SMP).


What else can I do here?

---

