---
title: "support alsa"
date: 2010-08-30
forum: Multimedia Software
---

### Post by c30tehran on 2010-08-30
i'll support alsa my sound or not


in windows
ich ac97
soundblaster 16

Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
        Subsystem: Giga-byte Technology Device 4385
        Flags: 66MHz, medium devsel
        Capabilities: <access denied>
        Kernel modules: i2c-piix4

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by c30tehran on 2010-08-31
Does ALSA support my sound card with the given information or the sound hangs forever?

---

### Post by c30tehran on 2010-10-06
alsa-info.sh

[http://paste.ubuntu.com/507164/](http://paste.ubuntu.com/507164/)

alsa-info.sh --bug

out:

[http://paste.ubuntu.com/507166/](http://paste.ubuntu.com/507166/)

after compile alsa :

[http://paste.ubuntu.com/507168/](http://paste.ubuntu.com/507168/)

info audio:

```
Realtek High Definition Audio

AMD SB710
realtek alc888 codec
high definition audio
2/4/5.1/7.1-channel
support for S/PDIF In/Out


Intel HDA driver
snd_hda_intel

```

---

### Post by c30tehran on 2010-10-08
thank you for help:popcorn:

---

### Post by lidex on 2010-10-08
Your alsa upgrade did not go well. Go here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
and follow directions for upgrading.

---

### Post by c30tehran on 2010-10-10
alsa-base.conf

[http://paste.ubuntu.com/509967/](http://paste.ubuntu.com/509967/)


aplay -l
aplay: device_list:223: no soundcards found...

> sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio

=======================================
sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mehri/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/mehri/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).



[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

---

