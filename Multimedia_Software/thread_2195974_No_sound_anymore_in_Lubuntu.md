---
title: "No sound anymore in Lubuntu"
date: 2013-12-27
forum: Multimedia Software
---

### Post by jdrc on 2013-12-27
Hi - I just turned on my computer (Lubuntu 13.10) for the first time in a couple of weeks, and there's no sound.  I checked Pandora and Grooveshark across Chromium and Firefox, and then tried a song from the hard drive on Gnome MPlayer. Tried with headphones and the computer's speakers.  Nothing.

Any suggestions?

Thanks!
John

---

### Post by jdrc on 2013-12-27
I'm at even more of a loss now: I reinstalled Lubuntu to see if that would solve the problem, but before I did, I ran it off of USB for a few minutes, and the sound worked fine on USB.  Now that I've reinstalled, the sound is gone again!

---

### Post by Yellow Pasque on 2013-12-27
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by jdrc on 2013-12-27
Thanks!

Here you go: [http://www.alsa-project.org/db/?f=0c74449e99d5712e6a99094728e970dea672f49d](http://www.alsa-project.org/db/?f=0c74449e99d5712e6a99094728e970dea672f49d)

---

### Post by Yellow Pasque on 2013-12-27
I see this in dmesg:
```
[   16.407268] hda-codec: out of range cmd 0:20:400:ffffffff
```

Also:
```
[ 1531.417674] hda-intel: Invalid position buffer, using LPIB read method instead.
```

To solve the latter issue, I would run
```
echo "options snd-hda-intel position_fix=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

---

### Post by jdrc on 2013-12-27
Thanks so much for your follow-up, but I don't know what to do with these.  I'm not even sure what "echo" and "sudo" mean - are they commands, programs, something else?  I've googled them, but I'm in over my head.  Is there a basic fix here, or am I destined not to have audio on this computer?

---

### Post by Yellow Pasque on 2013-12-28
Just copy/paste that whole command into a terminal. If you need more assistance in doing that, then you should be posting in the beginner's forum.

---

