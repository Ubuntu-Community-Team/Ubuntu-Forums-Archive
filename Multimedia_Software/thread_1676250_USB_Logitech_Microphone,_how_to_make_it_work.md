---
title: "USB Logitech Microphone, how to make it work"
date: 2011-01-26
forum: Multimedia Software
---

### Post by Vetal_ca on 2011-01-26
I have a usb Logitech Microphone. Goal is to make it to work in XBMC for Karaoke. But at the beginning I'd like it to be visible in Ubuntu, Pulse (?)

1. It is present in my USB devices:
```

vetal@smedia:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 008: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone
Bus 002 Device 007: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 002 Device 006: ID 413c:2006 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:1004 Dell Computer Corp. 
Bus 002 Device 004: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 002 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vetal@smedia:~$ 

```2. It is present as an ALSA device (1.00.23):
```

vetal@smedia:~$ cat /proc/asound/devices   0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
  6: [ 0- 2]: hardware dependent
  7: [ 0- 3]: hardware dependent
 19: [ 0- 3]: digital audio playback
 23: [ 0- 7]: digital audio playback
 24: [ 0- 8]: digital audio playback
 25: [ 0- 9]: digital audio playback
 32: [ 1]   : control
 33:        : timer
 56: [ 1- 0]: digital audio capture

```3. It is visible and unmuted for alsamixer:


[IMG]http://vetal.ca/Download/img/Linux/AlsaMixer.png[/IMG]

4. And it is present in Gnome Alsa Mixer:

[IMG]http://vetal.ca/Download/img/Linux/GNOME_ALSA_Mixer.png[/IMG]


5. But it is not present in Sound options as an input device:

[IMG]http://vetal.ca/Download/img/Linux/Sound_Preferences.png[/IMG]


 I am a bit new to this, but in order my HDMI audio device, presented in ALSA to be visible in Ubuntu sound properties, I had to enable it for Pulse audio:

```

/etc/pulse/default.pa

#Loading module for hdmi multichannel sound
load-module module-alsa-sink device=hw:0,7 channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe

```If I understand it right, I need to do something like this for Mic, but what?

To get my ultimate goal, I found something like 
```

load-module module-loopback

```But it didn't work at all:
```

vetal@smedia:~$ pactl load-module module-loopback
Connection failure: Connection terminated

```Any ideas? Thank you

---

### Post by Vetal_ca on 2011-01-26
Geez, whole day of browsing tons of forums and no answer.

One long written post made everything clear in my head. Solution been right there at the last lines, popped in my head 5 minutes after the post:

/etc/pulse/default.pa
```

load-module module-alsa-source device=hw:1,0
load-module module-loopback

```

And it worked right away with pactl command!

---

### Post by rhinds1369 on 2011-01-28
Nice!

---

