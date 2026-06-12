---
title: "How to troubleshoot skipping sound/audio"
date: 2009-01-12
forum: Multimedia Software
---

### Post by Kimos on 2009-01-12
So I'm looking for suggestions on how to start troubleshooting a problem with my sound.

Audio works fine, but if I'm listening to music for an extended period of time (something I do often) the sound will skip every five or ten minutes. Just a small gap. A hiccup or a moment of silence. Enough to notice.

I'm using 8.04, listening to mp3s using Amarok for the most part. Nothing shows up in dmesg. The errors happen so infrequently that I can't recreate them to try to track them.

I have no other issues with sound so I'm guessing that it's not a sound card/driver problem, though I'm not writing that off. I know that I can do audio playback through other applications and see if the problem occurs, but I'm hoping there are logs or something that I can monitor that would give me more definitive results.

Thanks!

FYI, I'm running on x86 32-bit:

```

kevin@sephiroth:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kevin@sephiroth:~$ cat /proc/asound/modules
 0 snd_via82xx
kevin@sephiroth:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Nov 25 2008 for kernel 2.6.24-22-generic (SMP).
kevin@sephiroth:~$ cat /proc/version
Linux version 2.6.24-22-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 18:32:42 UTC 2008

```

---

### Post by markbuntu on 2009-01-12
Where are these tracks coming from?
Are they from your machine or shoutcast or something?

---

### Post by Kimos on 2009-01-12
They're coming from an ext3 mounted local drive. I can safely eliminate any network problems.

---

### Post by markbuntu on 2009-01-12
It may be that something is taking a higher system priority than amarok which will cause this to happen. This will not generally create error messages as the system is operating properly.

An e-mail checker will do this, so will update manager. I always know when update manager starts running because I get a glitch in my audio but usually I am listening to streams from shoutcast.

Anyway, I think that is the path you need to follow. System monitor can help you with that. On my system pulseaudio is running with a nice of -11 and amarok is nice 0.

---

### Post by Kimos on 2009-01-14
Thanks. I'll start there.

---

