---
title: "trying to get sound working"
date: 2011-03-02
forum: Multimedia Software
---

### Post by NJames99 on 2011-03-02
I have no sound in Ubuntu 10.04. I'm dual-booting with Windows 7 and sound works in Windows.

I was working through the SoundTroubleshooting guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and got as far as checking the ALSA-configuration.txt for my codec, I figured out that I need to look in the HD-Audio-Models.txt here: [http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/HD-Audio-Models.txt;h=abffd4112327b97e856c22b6b03244f7471ab63b;hb=1cdf06bcd91e0c180efbc43f03ce0a1cf68ae8ec](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/HD-Audio-Models.txt;h=abffd4112327b97e856c22b6b03244f7471ab63b;hb=1cdf06bcd91e0c180efbc43f03ce0a1cf68ae8ec)
But, I don't see my codec ALC887 listed.

Any help here?

oh, my ALSA script info is available here: [http://www.alsa-project.org/db/?f=fc650d14c87f725b68123b01229cd2d43c8ebfbe](http://www.alsa-project.org/db/?f=fc650d14c87f725b68123b01229cd2d43c8ebfbe)

---

### Post by lidex on 2011-03-02
Do you really have 5 audio jacks? Please post this output:
```
cat /etc/modprobe.d/alsa-base.conf
```

I would suggest re-installing alsa at this point as well:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by NJames99 on 2011-03-02
The motherboard has 3 jacks in the back (line in, line out, mic in) and the case has two jacks in the front that are connected to a Front Panel Audio Header on the motherboard (mic in, headphones).

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
options snd-hda-intel model=5stack

```The last line was added to the file by me, following a suggestion seen elsewhere. I have tried model=3stack, model=3stack-digout, both to no effect.

I will run the reinstall command you suggest now. Thanks for taking some time to look at this.

---

### Post by lidex on 2011-03-02
So it's obviously not working, go ahead and remove it and carry on with the re-install.
Not sure why the modprobe options show twice in your alsa-info; what do you get for this:
```
ls /etc/modprobe.d/
```

---

### Post by NJames99 on 2011-03-02
I ran the reinstall line you posted, and rebooted. No noticeable difference however. I have also removed the last line in /etc/modprobe.d/alsa-base.conf and set Sound Preferences>Hardware Internal Audio device back to the original setting of Analog duplex. No sound so far.

```
ls /etc/modprobe.d/
```results in this:
```
alsa-base.conf          blacklist.conf              blacklist-oss.conf
alsa-base.conf.save     blacklist-firewire.conf     blacklist-watchdog.conf
alsa-base.save          blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf

```blacklist-oss.conf shows in a teal font rather than black like the rest.

---

### Post by lidex on 2011-03-03
Now I see. Remove alsa-base.conf.save and alsa-base.save  or at least move them to a different directory. Most anything in that directory seems to get read.

---

### Post by NJames99 on 2011-03-03
Beautiful! Now I have sound. All seems to be working now.

---

