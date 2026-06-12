---
title: "Plantronics DSP v4 Audio Interface"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Stratty on 2008-11-12
New Linux user and I am enjoying the experience so far.  One issue remains with my Ubunto 8.04, sound.  I have scoured the forums and internet looking for potential solutions.  I have battled with ALSA, Pulse Audio, and the like without resolution so I come to you for additional advice.


Setup: Ubunto 8.04, Plantronics USB headphone (GameCom1)
Symptoms:  I hear the startup sound but it goes static and clips the ending.  From that point on sound does not work.  Almost like there is a conflict on system startup.

Details:

From the syslog:
```

Nov 11 23:26:05 Jason-Linux kernel: [15758.383940] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:916: timeout: still 2 active urbs..

Nov 11 23:26:15 Jason-Linux pulseaudio[7102]: module-alsa-sink.c: Failed to set hardware parameters: Input/output error

Nov 11 23:26:15 Jason-Linux kernel: [15768.385904] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1345: 2:1:2: usb_set_interface failed
```

Additional details:
```
jason@Jason-Linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

jason@Jason-Linux:~$ lsusb
Bus 002 Device 002: ID 047f:0ca1 Plantronics, Inc. USB DSP v4 Audio Interface
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  

jason@Jason-Linux:~$ cat /proc/asound/cards
 0 [Headset        ]: USB-Audio - Plantronics Headset
                      Plantronics Plantronics Headset at usb-0000:00:0b.0-1, full speed

jason@Jason-Linux:~$ asoundconf listNames of available sound cards:
Headset
```


I am open to any suggestions and look forward to your advice.

Stratty

---

### Post by Stratty on 2008-11-12
Update - more information:

If I turn off all startup sounds and open System>Preferences>Sound and hit the "test" option I can hear about 1 second of test tone before it goes silent.  

The following error is generated in the syslog:

```
Nov 12 20:43:19 Jason-Linux kernel: [ 3617.329360] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:916: timeout: still 1 active urbs..
```

---

### Post by markbuntu on 2008-11-13
Have you looked at these?

[http://www.xantius.com/articles/dsp-400.php](http://www.xantius.com/articles/dsp-400.php)

[https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls](https://help.ubuntu.com/community/PlantronicsUSBHeadsetControls)

You could also try plugging the headset in after you boot instead of having it plugged in when you boot.

---

### Post by PingMetal on 2010-06-05
Hi, i'm experiencing the same kind of problem, but it's if i turn on my USB microphone. I'm getting a: "timeout: still 8 active urbs.." in console mode when it's turned on and after few seconds, all the USB devices (keyboard and mouse) don't respond anymore. I hope to find a solution, because i absolutely need my microphone.

---

