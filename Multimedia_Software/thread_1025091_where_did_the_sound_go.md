---
title: "where did the sound go?"
date: 2008-12-29
forum: Multimedia Software
---

### Post by raucous on 2008-12-29
strange problem: When i turn my laptop on i can hear the audio coming from all sources such as youtube, audacious, etc., but if i leave it on for a few hours and come back to it i cant hear any sound. all of the volume controls are up and the monitoring bars move across the screen so i know the song is playing. When i restart im back to normal. 

any suggestions?

thanks.

8.10

---

### Post by markbuntu on 2008-12-29
This is a bug with the alsa HDA driver for some chips. From a terminal type

alsa force-reload

and that should get your sound back without having to reboot. Hopefully this will be fixed soon.

---

### Post by coryodo28 on 2008-12-29
I tried that and get this error message:

coryodo@ubuntu:~$ alsa force-reload
Terminating processes: 6597.
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-emu10k1-synth snd-emux-synth snd-seq-virmidi snd-seq-midi-emul snd-emu10k1 snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-mpu401-uart snd-page-alloc snd-util-mem snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).


PLease help, thank you

---

### Post by markbuntu on 2008-12-29
Oh sorry, you need to have root priveleges to do this, try

sudo alsa force-reload

---

