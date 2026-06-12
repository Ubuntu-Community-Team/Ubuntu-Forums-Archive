---
title: "JACK and USB soundcard"
date: 2013-02-16
forum: Multimedia Software
---

### Post by Wehrdo on 2013-02-16
I want to use rosegarden for composing music, because of its strong notation editing abilities, but to get sound, I need to use JACK. I have a USB soundcard (uses the CM106 chipset) and I can't start a JACK session when selecting hw:1,0 which aplay -l says is my USB soundcard. When I try to start it, here's the error:

```
19:20:11.386 Patchbay deactivated.
19:20:11.387 Statistics reset.
19:20:11.391 ALSA connection change.
19:20:11.402 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
19:20:11.413 ALSA connection graph change.
19:21:10.879 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sat Feb 16 19:21:10 2013: Starting jack server...
Sat Feb 16 19:21:10 2013: JACK server starting in realtime mode with priority 10
Sat Feb 16 19:21:10 2013: control device hw:1
Sat Feb 16 19:21:10 2013: control device hw:1
Sat Feb 16 19:21:10 2013: Acquired audio card Audio1
Sat Feb 16 19:21:10 2013: creating alsa driver ... hw:1,0|hw:1,0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Sat Feb 16 19:21:10 2013: control device hw:1
Sat Feb 16 19:21:10 2013: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Sat Feb 16 19:21:10 2013: ALSA: final selected sample format for capture: 16bit little-endian
Sat Feb 16 19:21:10 2013: ALSA: use 2 periods for capture
Sat Feb 16 19:21:10 2013: ALSA: final selected sample format for playback: 16bit little-endian
Sat Feb 16 19:21:10 2013: ALSA: use 2 periods for playback
Sat Feb 16 19:21:10 2013: [1m[31mERROR: ALSA: could not start playback (Broken pipe)[0m
Sat Feb 16 19:21:10 2013: [1m[31mERROR: Cannot start driver[0m
Sat Feb 16 19:21:10 2013: [1m[31mERROR: JackServer::Start() failed with -1[0m
Sat Feb 16 19:21:10 2013: [1m[31mERROR: Failed to start server[0m
Sat Feb 16 19:21:10 2013: control device hw:1
Sat Feb 16 19:21:10 2013: Released audio card Audio1
Sat Feb 16 19:21:10 2013: control device hw:1
Sat Feb 16 19:21:12 2013: Saving settings to "/home/david/.config/jack/conf.xml" ...
19:21:14.932 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

The funny thing is I can start JACK with my built in soundcard, but I want the improved performance of the external one.

I've spent hours searching for an answer, but nothing has worked yet. I'm on the verge of going back to my mac with Garageband. Any ideas?

Thanks!

---

### Post by Yellow Pasque on 2013-02-16
Please post output of lsusb
```
sudo update-usbids
lsusb
```

---

### Post by Wehrdo on 2013-02-16
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 004: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 008 Device 003: ID 1234:3235 Brain Actuated Technologies 
```

Weird, "Brain Actuated Technologies" must be my Alesis QX25 MIDI keyboard; it's the only other USB device.

---

### Post by Yellow Pasque on 2013-02-16
So it looks like the card is plugged into a USB 1.1 hub. Try other USB ports (idea  from [https://ardour.org/node/3492#comment-26182](https://ardour.org/node/3492#comment-26182) )

---

### Post by Wehrdo on 2013-02-16
That was the issue! Switched ports, and it works great. I don't think my motherboard manual made any mention of USB 1.1 ports, and I don't have any external hubs connected, so that's strange.

Thank you very much! Now I can start making music, not error messages.

---

