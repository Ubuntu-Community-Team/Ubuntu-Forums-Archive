---
title: "[SOLVED] no sound with Emu 0404 USB"
date: 2008-11-20
forum: Multimedia Software
---

### Post by jodaka on 2008-11-20
I've got a notebook with some integrated crap ac97 sound. Recently i've bought Emu 0404 USB and tested it under other box with windows. It sounds great

after pluggin it into my linux box dmesg told me that usb-audio detected. That was a good part. I've tried to make 0404 my default soundcard by changing index in /etc/modprobe.d/alsa-base. That worked

now aplay -l gives me:

```
**** List of PLAYBACK Hardware Devices ****
card 0: USB [E-MU 0404 | USB], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: USB [E-MU 0404 | USB], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've unmuted 0404 in alsamixer.

My next step was to actually try play some mp3. So, i've selected 'ALSA' in System > Preferences > Sound but mp3 still plays using integrated ac97. Don't know why... 

i've tried selecting OSS as the default in System>Preferences>Sound... and I even was able to listen so some sound (but... that was yesterday... today I only hear some ugly noise if I try select OSS)

I've read tons of manuals, but still don't understand, how sound system works in gnome. Why when it configured to use ALSA it still play sound using integrated AC97 (while aplay says default is 0404)

i saw some notes that 0404USB run smooth out of the box in Fedora 9. Will download livecd and check this soon...

any ideas?

---

### Post by kostkon on 2008-11-20
Which version of Ubuntu are you using?

---

### Post by jodaka on 2008-11-20
> **kostkon said:**
> Which version of Ubuntu are you using?

oh sorry... I thought that it's enought to set ubuntu version in profile :(

anyway, I'm using Ubuntu 8.10 rather fresh install (not an update)
alsa Version: 1.0.17.dfsg-2ubuntu1

well... I've tried also asoundconf-gtk to switch soundcards - no effect.

and just tried Fedora9 LiveCD -- no luck for me. It just keep using my integrated crap :)
And worst of all -- my notebook don't have an option to disable ac97 in bios.

I guess I'll end up with manual kernel recompile with disabled ac97 :-\

---

### Post by psyke83 on 2008-11-20
You're approaching the problem from the wrong angle - Intrepid uses PulseAudio by default. This means that ALSA's asound.conf and module indexes do not apply.

Follow this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Read the FAQ and Appendix B to learn how to set default sinks (playback devices) in PulseAudio.

P.S. Choosing the ALSA playback driver in System/Preferences/Sound won't change much. Intrepid's ALSA libraries have been patched so that ALSA applications transparently remap audio to PulseAudio via the PulseAudio ALSA plugins.

---

### Post by jodaka on 2008-11-20
> **psyke83 said:**
> 
P.S. Choosing the ALSA playback driver in System/Preferences/Sound won't change much. Intrepid's ALSA libraries have been patched so that ALSA applications transparently remap audio to PulseAudio via the PulseAudio ALSA plugins.
wow... that explains everything :)

ok, now after some shaman dances i can hear some kind of sound from 0404 USB using PulseAudio. But sound quality is crap... but I believe that's another problem with descritization.

---

