---
title: "Sound doesnt work"
date: 2009-02-16
forum: Multimedia Software
---

### Post by Lalesvi on 2009-02-16
Hi. I cant make the sound work in my computer, and I dont know why... I have already tried all the different possibilities I know to make it work! Do you have any suggestion on what I could try next? (I am using Ubuntu 7.10)

I have permissions to listen the audio:
```

gatv@gatv-laptop:~$ groups
gatv adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev

```

The computer recognizes the sound card:
```

gatv@gatv-laptop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```
```
gatv@gatv-laptop:~$ asoundconf list
Names of available sound cards:
Intel 

```
```

gatv@gatv-laptop:~$ sudo lspci -v
(...)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Toshiba America Info Systems Unknown device ff50
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f0800000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [70] Express Unknown type IRQ 0

```

Everything seems to work fine, except for the fact that I can not hear anything. Do you have any suggestion? Thank you very much.

---

### Post by itang sanjana on 2009-02-16
Hello mine also Intel.

Have you check your sound preferences?
system > preferences > sound
Make sure everything work fine by clicking each test buttons.

Also check for ALSA mixer. Make sure Master & PCM set on properly level and not muted.

HTH

---

### Post by halovivek on 2009-02-16
Hi
please check this thread, you can get solution from this [one.]("http://ubuntuforums.org/showthread.php?t=1005416")

---

### Post by Lalesvi on 2009-02-16
The last test button ("Sound capture: ALSA") does work properly. An error window opens: "We couldn't build the test pipe for "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat""

The other test buttons don't reproduce any sound.

> Also check for ALSA mixer. Make sure Master & PCM set on properly level and not muted.
What I have tried to check if the errors were in the mixer with "aumix", "alsamixer", but they were working fine... Do you know another way to check it?

---

### Post by Lalesvi on 2009-02-18
Just in case someone have the same problem, I solved it here:
[https://bugs.launchpad.net/ubuntu/+bug/159045](https://bugs.launchpad.net/ubuntu/+bug/159045)

Here is a list of the tipical things you can do to repear the sound:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

