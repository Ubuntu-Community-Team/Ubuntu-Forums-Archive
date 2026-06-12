---
title: "hda-intel soundcard: garbled sound since Hardy upgrade"
date: 2008-04-26
forum: Multimedia Software
---

### Post by fuzzypig on 2008-04-26
Since I updated to Hardy Heron yesterday, all sound on my laptop has been hopelessly garbled. The sound could best be described as 'fuzzy' (The sound is full of noise).

```
fuzzypig@fp-ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0340000 irq 21
 1 [VirMIDI        ]: VirMIDI - VirMIDI
                      Virtual MIDI Card 1
```

```
fuzzypig@fp-ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)
```

```
fuzzypig@fp-ubuntu:~$ lspci | grep -i "audio"
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

```
fuzzypig@fp-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
fuzzypig@fp-ubuntu:/etc/modprobe.d$ cat alsa-base
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
# hda-intel card
options snd-hda-intel model=laptop
```

("options snd-hda-intel model=laptop" is needed for the headphone jack to work.)

---

### Post by fuzzypig on 2008-04-27
bump (updated)

---

### Post by Kcrsh10 on 2008-04-28
Hi, I have a similar intel sound card, and had no sound after upgrade. I resolved this by grabbing the 386 kernel. Dont know if it'll help but the links here: [http://ph.ubuntuforums.com/showthread.php?t=720043&page=5&](http://ph.ubuntuforums.com/showthread.php?t=720043&page=5&)

---

### Post by fuzzypig on 2008-04-28
I don't think the same thing would work, because I do have sound, it's just garbled.

If it helps, here is a recording of audio playback from my laptop. (This is supposed to sound like a piano.): [http://www.mediafire.com/?dnwraijob2x](http://www.mediafire.com/?dnwraijob2x)

---

### Post by msrourke on 2008-04-29
> **fuzzypig said:**
> I don't think the same thing would work, because I do have sound, it's just garbled.

If it helps, here is a recording of audio playback from my laptop. (This is supposed to sound like a piano.): [http://www.mediafire.com/?dnwraijob2x](http://www.mediafire.com/?dnwraijob2x)

Well, I can't help, I haven't figured it out yet myself. I have an HP laptop with Conexant HDA. Same problem. I just decided to do away with the dual boot and go strictly Ubuntu. Braking hard till I figure this one out... :(

---

### Post by novus721 on 2008-04-30
I had the same problem, and I use a normal PC. But I MAY have found the solution!

I went to System > Prefs > Volume Control > Switches (tab) and I unchecked the output jack.

I honestly don't know exactly what that did, but the noise immediately went away and now my sound works as good as it did before I upgraded - FINALLY.

Also, I don't know how much this matters but my Sound Prefs are set to PulseAudio across the board minus the mic. Even though they are set as such, I can play different audio files off of different playback platforms (vlc, youtube, gxine, etc).

Hope this helps someone!!

---

### Post by fuzzypig on 2008-04-30
I don't have an output jack switch. All I have is an IntMic switch which can't be unchecked. You think I should file a bug report?

---

### Post by docem on 2008-05-01
gday I have the same hardware per
cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)
I also cannot disable intmic, but I found a solution
by using alsamixer I noticed the PCM volume was 100% while the Master was 50% by lowering the PCM to the same level as the Master the problem was fixed! Any lower setting seemed to work...
hope this helps

---

### Post by fuzzypig on 2008-05-01
The PCM fix worked.

Strange thing is, afterwards I raised the PCM back to 100%, and the sound still worked fine!

Strange. I wonder if I'll have to do this again after reboot. Maybe I can write a script.


---


SOLVED. The fix remains after reboot.

---

