---
title: "Microphone won't stay muted (Karmic)"
date: 2010-02-05
forum: Multimedia Software
---

### Post by martron88 on 2010-02-05
I've got an asus a8js laptop and since installing karmic, the built in microphone is permanently on.  Every once in a while I brush my finger of the mic unintentionally and it makes some mad feedback.

I've ruled out that this is caused by pulseaudio, the problem occurs when pulseaudio is off (pulseaudio --kill) and I've set .asoundrc to go straight through the hardware.

My first thought was to check alsamixer, but I muted (capture, mic, mic boost set to 0) it in there to no avail.  Consequently, any time I move a slider (any one, PCM, mic, Front...) the microphone mutes for 3 to 15 seconds and then is suddenly live again.

Here's my .asoundrc
```

pcm.!default {
	type plug
  slave { pcm "intel" }
}

pcm.intel {
	type hw
	card 0
}

ctl.mixer0 {
    type hw
    card 0
}

ctl.intel {
	type hw           
	card 0
}


```

In all the soundcard works fine, it's just that the mic is always on and I can't seem to set it otherwise.

Any thoughts?  Similar bugs people have found?  I haven't managed to find anything that's quite like what I'm encountering.

---

### Post by lidex on 2010-02-05
Try these links and update us:
[http://ubuntuforums.org/showthread.php?t=180022]("http://ubuntuforums.org/showthread.php?t=180022")
[http://ubuntuforums.org/showthread.php?t=1181130]("http://ubuntuforums.org/showthread.php?t=1181130")

---

### Post by martron88 on 2010-02-08
Neither of those posts were too helpful.  Alsamixer shows 'Mic' and 'Mic boost' to both be set to 0 (off).  In fact, I went through it and muted everything, including 'Master' and 'Headphone' and I can still hear the mic through my speakers.

I've narrowed down the problem a bit though.  I just shut down alsa (with sudo /etc/init.d/alsa-utils stop ) and the mic is still active.

... Some time passed.

Turns out this is the work of OSS.  I installed aumix and changed the mic volume setting in there to 0 while alsa was off.  Now the mic is properly muted!

---

### Post by martron88 on 2010-02-08
Well I might not be completely right.  When I started alsa back up again, the mic became live.  All I had to do was move the mic slider back to 0 in aumix.

---

### Post by lidex on 2010-02-08
> **martron88 said:**
> Neither of those posts were too helpful.  Alsamixer shows 'Mic' and 'Mic boost' to both be set to 0 (off).  In fact, I went through it and muted everything, including 'Master' and 'Headphone' and I can still hear the mic through my speakers.

I've narrowed down the problem a bit though.  I just shut down alsa (with sudo /etc/init.d/alsa-utils stop ) and the mic is still active.

... Some time passed.

Turns out this is the work of OSS.  I installed aumix and changed the mic volume setting in there to 0 while alsa was off.  Now the mic is properly muted!

That was the low hanging fruit. My next recommendation involves editing your alsa-base.conf and/or upgrading alsa. What's the output of this command:
```
head -n 1 /proc/asound/card0/codec*
```

---

### Post by martron88 on 2010-02-12
The output of that command is:

```
~$ head -n 1 /proc/asound/card0/codec*

==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1986A

==> /proc/asound/card0/codec#1 <==
Codec: Generic 1543 Si3054

```

I'm not sure what that means.  Maybe one is for the modem?

I've taken a look at alsa-base.conf and I'm not exactly sure what to do with it although it's laid out in a straightforward way.  I wouldn't mind just disabling the laptop mic altogether since I generally plug in a headset anyway for better sound.

---

### Post by lidex on 2010-02-12
I've got an idea. Can you post your alsa-base.conf?

---

### Post by VertexPusher on 2010-02-12
> **martron88 said:**
> I've ruled out that this is caused by pulseaudio, the problem occurs when pulseaudio is off (pulseaudio --kill) and I've set .asoundrc to go straight through the hardware.
Are you sure? As far as I know, pulseaudio is configured to auto-spawn as soon as it is killed (or crashes). Furthermore, pulseaudio is known to reset ALSA volume levels on startup according to a set of configuration files located in /usr/share/pulseaudio/alsa-mixer. If you launch alsamixer without passing a hardware PCM name or number (see the -D and -c options), this may trigger pulseaudio's auto-spawn as well.

Another application known to automatically change volume levels, especially mic volume, is Skype.

ALSA never changes mixer settings by itself.

---

### Post by martron88 on 2010-02-12
> **lidex said:**
> I've got an idea. Can you post your alsa-base.conf?

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
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

---

### Post by martron88 on 2010-02-12
> **VertexPusher said:**
> Are you sure? As far as I know, pulseaudio is configured to auto-spawn as soon as it is killed (or crashes). Furthermore, pulseaudio is known to reset ALSA volume levels on startup according to a set of configuration files located in /usr/share/pulseaudio/alsa-mixer. If you launch alsamixer without passing a hardware PCM name or number (see the -D and -c options), this may trigger pulseaudio's auto-spawn as well.

Another application known to automatically change volume levels, especially mic volume, is Skype.

ALSA never changes mixer settings by itself.

I'm 90% sure.  A while ago I configured pulseaudio to use jack with my firewire soundcard and part of that process was to disable pulseaudio's auto respawn.

---

### Post by martron88 on 2010-02-12
I actually think I solved the issue last night.  I had configured a faulty .asoundrc which I think was defining two streams for pulse to use.  The solution?  Delete .asoundrc (or mv .asoundrc .asoundrc.bad) and use the default configuration on reboot (or restart of the x-server).

I knew this was probably the result of a bunch of noodling I've been doing with alsa, pulseaudio and jack so I think I have a solution that gets them working.

I am still interested in disabling the onboard mic altogether.  Even if I plug in a headset to the mic jack, the onboard stays on, which makes skype conversations lousier than they should be.

---

