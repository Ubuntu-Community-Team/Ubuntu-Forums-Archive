---
title: "Magically noise apear"
date: 2008-11-23
forum: Multimedia Software
---

### Post by sakinho on 2008-11-23
Hi all!

I use ubuntu since 1 year, sound allways went well (excep the microphone) but last week I turn on my computer and instead sound I hear noise. I don't know the cause and I have been proving differents configurations of my alsa driver (intel) and nothing happends, my computer thinks it is playing real audio because system sounds, music, films, test sound (from alsa config) and whatever sound like noise, and if I up sound level, noise go up and down the same thing.

Or course, I have proved with headphones and the same result. Even I have try the sound with another OS and It work perfect with the speakers of my laptop and with headphones.

I have seen a lot of forum threads and googling but I have not read something like this. Can yu help me?

Mistery continues... :(

PS: Ubuntu 8.10

---

### Post by ramaswamyps on 2008-11-23
try pcm lower levels
try running alsaconf again

---

### Post by sakinho on 2008-11-24
**Semi-solved**, I erase ALSA state: /var/lib/alsa/asound.state

Then I forced reload ALSA (reload don't work) 
```
sudo alsa force-reload
```

But WARNINGS appear and I think problem is there:
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sak/.gvfs
      Output information may be incomplete.
Terminating processes: 6177 6281lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sak/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sak/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sak/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-intel snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-intel snd-pcm snd-timer snd-page-alloc.

```

Thanks ramaswamyps and [GLUG]("http://glug.es").

---

