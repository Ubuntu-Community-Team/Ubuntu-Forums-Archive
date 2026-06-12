---
title: "Sound - no devices, no sound"
date: 2012-10-12
forum: Multimedia Software
---

### Post by Potkn on 2012-10-12
Hello everyone,
I am sorry to create a new thread about sound problems, but I'm desperate and none of the other threads has helped.

When I found out my netbook wouldn't play any sound, I started going through forums and tried out some shell codes to make it work. Result – now there are no sound cards whatsoever in the Sound menu. Also next to the sound icon, there are three dashes instead of “waves” and I cannot control volume.

Image: [http://postimage.org/image/i747pi3ft/](http://postimage.org/image/i747pi3ft/)

[IMG]http://postimage.org/image/i747pi3ft/[/IMG]

This is what it returns:

```
$ uname -a 
Linux dave 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux
```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices **** 
/usr/bin/pulseaudio: error while loading shared libraries: libpulsecommon-1.1.so: cannot open shared object file: No such file or directory 
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 

```
```

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.24.
```

```
$ head -n 1 /proc/asound/card*/codec#* 
==> /proc/asound/card0/codec#0 <== 
Codec: Realtek ID 269 

==> /proc/asound/card0/codec#1 <== 
Codec: Intel CedarTrail HDMI
```

What do I do?

---

### Post by Yellow Pasque on 2012-10-14
You probably removed or otherwise borked pulseaudio (because all of the low-level ALSA driver info looks okay). First thing I would do is purge puleaudio and reinstall it.
```
rm -rf ~/.pulse*
sudo apt-get purge pulseaudio
sudo apt-get install pulseudio
```
Then log out and back in. If that doesn't help, post pulse log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

