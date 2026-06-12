---
title: "No sound after restart?"
date: 2008-12-30
forum: Multimedia Software
---

### Post by BeastlyKings on 2008-12-30
My sound was working fine, nothing out of the ordinary, I restarted and now I have no sound..
When I adjust the volume from my keyboard, I can hear the rumble in my speakers, so I figure that mean the hardware and driver is fine?
Then why can't I hear any sound?
I opened System>Preferences>Sound and tested all the options, but still nothing..

Help?

---

### Post by linux_tech on 2008-12-30
try
```
sudo /etc/init.d/alsa force-reload
```

---

### Post by BeastlyKings on 2008-12-30
All I get is this:

tom@tom-desktop-810:~$ sudo /etc/init.d/alsa force-reload
sudo: /etc/init.d/alsa: command not found

---

### Post by linux_tech on 2008-12-30
How about 
```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start



```

---

### Post by BeastlyKings on 2008-12-30
Hmmm, still no sound, everything seems to be the same.

```
tom@tom-desktop-810:~$ sudo /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                 [ OK ] 
tom@tom-desktop-810:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
Terminating processes: 5671 5820lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-via82xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-mpu401-uart snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
tom@tom-desktop-810:~$ sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                    [ OK ] 
tom@tom-desktop-810:~$ 

```

Thanks for trying! Any other ideas?

---

### Post by BeastlyKings on 2008-12-30
bump

---

### Post by Rodney9 on 2008-12-30
My sound dissappeared today as well, after coming back from suspend.
I followed the steps above, but also to no avail.

---

### Post by BeastlyKings on 2009-01-01
bump

---

### Post by BeastlyKings on 2009-01-03
bump

---

