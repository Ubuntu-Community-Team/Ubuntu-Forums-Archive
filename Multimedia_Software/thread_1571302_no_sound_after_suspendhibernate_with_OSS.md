---
title: "no sound after suspend/hibernate with OSS"
date: 2010-09-09
forum: Multimedia Software
---

### Post by lionl on 2010-09-09
):P recently got ubuntu in the last couple of weeks, has been decent so far but the sound quality wasn't up to par so I decided to try and improve it by installing OSS (open source sound from this site: [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)) and removing pulseaudio. Basically I followed the walkthrough on this page to a T: [http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html)

Anyways after a reboot the new OSS thingy worked fine, sound quality was much better (although my max volume now is way lower than it was before, but thats only a minor problem). Unfortunately, whenever I suspend/hibernate my laptop the sound ceases to work on resume, which never used to happen before. Rhythmbox refuses to play (the little scroller stays still at the beginning of a song and won't move along the line) and there is no sound whatsoever from youtube, etc...

this is the lspci -v output for my sound card

```
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
	Subsystem: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f4010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

any help would be much appreciated because its a pain to have to reboot everytime i suspend. I've tried googling solutions but none of them seem to work, would it maybe have something to do with having OSS4 as the sound driver? also its probably worth mentioning I have the propietary ATI Radeon driver installed. i'm not linux-savvy so hopefully this won't require too much complexity to solve, thanks! :p

PS: heres my output when I do sudo alsa force-reload (which is suggested in some other threads for this problem)

```
user@laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
```

---

### Post by Yellow Pasque on 2010-09-09
OSS4 is known to be problematic with suspen. Before you suspend, run:
```
sudo soundoff
```
After you resume:
```
sudo soundon
```

> heres my output when I do sudo alsa force-reload 
You're using OSS4 (not ALSA), so running that command doesn't make sense..

---

### Post by lionl on 2010-09-09
cool that works great :D thanks
sorry I thought I still had alsa 'underneath' the OSS4 (like the oss4 was just a module for alsa or something) and i just removed pulseaudio
shame that ill have to do that every time i suspend/resume but could be worse i guess

---

