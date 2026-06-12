---
title: "alsamixer"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Sevy on 2008-08-02
Im having problems getting my m audio 2496 soundcard to work with alsa and wonder whether I can troubleshoot with alsamixer but am unable to launch it in the terminal.I get the following error-
sevy@sevy-desktop:~$ alsamixer
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_alsa.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
sevy@sevy-desktop:~$ 

How can I restore alsamixer?

Cheers

---

### Post by K2712 on 2008-08-02
to find the name of your sound card:

```
asoundconf list
```

append the name of your sound card to the following:

```
asoundconf set-default-card "insert card name here"
```

Hopefully that should fix it.

---

### Post by Sevy on 2008-08-02
I did the following but still get the same error

sevy@sevy-desktop:~$ asoundconf set-default card M2496
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

---

### Post by Sevy on 2008-08-02
bump:confused::)

---

### Post by K2712 on 2008-08-03
I apologize, the command should have been:

```
asoundconf set-default-card Intel
```

---

### Post by Yellow Pasque on 2008-08-03
M-Audio cards work much better with OSS4 (see link in sig)

---

### Post by Sevy on 2008-08-04
I tried asoundconf set-default-card Intel but still cant open alsamixer

Ive given oss a go and followed Temüjin's guide but being a newbie I am stuck on a basic one.I cant seem to cd to the oss file I downloaded.

> 6. Navigate to where you have the deb file saved (e.g. if it's your home dir, cd ~/ ). Note the name of the file will be oss-linux_4.0-1016_amd64.deb if you downloaded that version

Ive tried-
cd ~/oss-linux-4.0-1016_i386.deb    and
cd oss-linux-4.0-1016_i386.deb     but I get the error "not a directory"

What am I doing wrong??
Cheers

---

### Post by Sevy on 2008-08-04
Im stuck at the mo,I cant cd to the oss folder in my home folder and cant go back to how I had the sound so now there is no sound at all.
What am I doing wrong when I try to cd to oss-linux-4.0-1016_i386.deb???

---

