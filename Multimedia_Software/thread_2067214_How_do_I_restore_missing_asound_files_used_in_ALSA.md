---
title: "How do I restore missing asound files used in ALSA for 12.04"
date: 2012-10-06
forum: Multimedia Software
---

### Post by Robbyx on 2012-10-06
I use ALSA not pulse. I had it working the way I want and then started computer after an update and every time I try to play a video there is a report that the drivers are missing. This is an example:


Audio output failed:
The audio device "sysdefault:CARD=Intel" could not be used:
No such device.


Previously cat /proc/asound/modules showed three cards now it shows nothing.

These are the cards that seem to have lost all their content:
pcm ----no soundcards----
modules ---empty
hwdep   ---empty
cards   ---no soundcards ----

Without doing a system re-install is there a way of rebuilding the proc/asound files so that the soundcard entries are restored?

---

### Post by pbrane on 2012-10-06
I would think you could simply re-install alsa and libasound2. In a terminal 
```

sudo apt-get --reinstall install alsa
sudo apt-get --reinstall install libasound2

```

might work. Or you could use synaptic package manager to reinstall the packages.

---

### Post by Robbyx on 2012-10-06
I followed your suggestion and although the alsa files were restored the empty files in proc/asound have not been regenerated. I think I need to run some procedure that will recreate the missing device info files. I do not what to run.

---

### Post by pbrane on 2012-10-06
hmm, it seems that the drivers may not be loading. the files in /proc are created by the drivers. Did you reboot after re-installing? You may need to do that to get the drivers loaded.

---

### Post by Robbyx on 2012-10-06
I did reboot.

---

### Post by Yellow Pasque on 2012-10-06
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by greatsirkain on 2012-10-06
Think I did:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```followed by:
```
sudo apt-get update
```and then a reboot when I had similar problems :)

Edit: That was in 11.10

---

