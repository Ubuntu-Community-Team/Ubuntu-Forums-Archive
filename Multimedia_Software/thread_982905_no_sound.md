---
title: "no sound?"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Maximusmaximus on 2008-11-15
hello all out there i am new to ubuntu and i am having annoyingly persistent problems with my ALSA sounds driver which comes stock with ubuntu. i have just ousted all the sound software and downloaded some new ones through the add/remove programs list (this is how i got rid of them as well) and i still get the same problem

max@kev-desktop:~$ alsa mixer
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
max@kev-desktop:~$ /sbin/alsa force-reload
Terminating processes: 5936 7064.
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-rtctimer snd-emu10k1-synth snd-emux-synth snd-seq-virmidi snd-seq-midi-emul snd-emu10k1 snd-hda-intel snd-ac97-codec snd-pcm-oss snd-seq-dummy snd-mixer-oss snd-seq-oss snd-seq-midi snd-pcm snd-rawmidi snd-page-alloc snd-util-mem snd-seq-midi-event snd-hwdep snd-seq snd-timer snd-seq-device.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
max@kev-desktop:~$ 

i know it says it has nothing to load but according to the add/remove program it says everything is installed and good to go (i have also done a computer restart) and yet nothing come up, the volume control is also erratic and quits unexpectedly a lot. 

for anyone who can help it is greatly apprecited

---

