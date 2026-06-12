---
title: "OSS4 in Ubuntu 10.04 Lucid"
date: 2010-05-16
forum: Multimedia Software
---

### Post by mgol on 2010-05-16
I'm still unable to configure OSS4 properly. I removed ALSA and PulseAudio completely (including alsa-base etc.), installed oss4-gtk and oss4-dkms from this PPA:
[https://launchpad.net/~sevenmachines/+archive/release+1](https://launchpad.net/~sevenmachines/+archive/release+1)
upgraded packages from this PPA:
[https://launchpad.net/~dtl131/+archive/ppa/](https://launchpad.net/~dtl131/+archive/ppa/)
and:
1) external speakers doesn't work; even if connected, sound goes out of internal speakers,
2) the only way I could actually hear anything was via:
```
osstest -lV
```
mplayer with -ao oss doesn't work either.

How to make it work at all?

I use Intel HD Audio:
```

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```
oss modules seems loaded:
```

$ lsmod | grep -i oss
oss_usb               110747  4 
oss_hdaudio           146671  8 
osscore               571433  6 oss_usb,oss_hdaudio

```

---

### Post by lidex on 2010-05-16
Check out these links for OSS:
[http://ubuntuforums.org/showthread.php?t=1420745]("http://ubuntuforums.org/showthread.php?t=1420745")
[http://ubuntuforums.org/showthread.php?t=1355676]("http://ubuntuforums.org/showthread.php?t=1355676")
[http://ubuntuforums.org/showthread.php?t=1217259]("http://ubuntuforums.org/showthread.php?t=1217259")
[http://ubuntuforums.org/showthread.php?t=866106]("http://ubuntuforums.org/showthread.php?t=866106")

---

