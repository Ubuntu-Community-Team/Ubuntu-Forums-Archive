---
title: "Mixxx Won't Open"
date: 2007-10-31
forum: Multimedia Production
---

### Post by ghindo on 2007-10-31
I'm trying to use Mixxx, but whenever I launch the program, it simply won't launch.  Two windows open, but very briefly, and close almost immediately.  I have tried reinstalling, but to no avail.  Help?

---

### Post by archivator on 2007-11-01
Open up a terminal and type ```
mixxx
``` in it. Then, post the output to this thread ;)

---

### Post by ghindo on 2007-11-01
```
Debug: Starting up...
Debug: Api name: OSS
Debug: Api name: ALSA
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Debug: The track /home/michael/Music/Cut Chemist/The Garden/03 Storm (Feat. Edan And Mr. Lif).mp3 was not found
Debug: The track /home/michael/Music/Cut Chemist/The Garden/01 The Garden (Album Version).mp3 was not found
Debug: playlist name Default
Debug: The track /home/michael/Music/Cut Chemist/The Garden/03 Storm (Feat. Edan And Mr. Lif).mp3 was not found
Debug: The track /home/michael/Music/Cut Chemist/The Garden/01 The Garden (Album Version).mp3 was not found
Debug: MidiObjectOSS: No MIDI devices available.
Debug: PowerMate: write(): Bad file descriptor
Debug: PowerMate: write(): Bad file descriptor
Debug: m_pHercules init: 137612360
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root.
Debug: Hercules device (-1) not found!
Debug: Midi OK (Workaround not required)
Debug: pitch true
Debug: PortAudio: getDeviceID(/dev/dsp (channel 1))
Debug: PortAudio: getDeviceID(/dev/dsp (channel 2))
Debug: PortAudio: getDeviceID(None)
Debug: PortAudio: getDeviceID(None)
Debug: PortAudio: kiMaxFrameSize: 1024, iLatencyMSec: 49
Debug: PortAudio: id -1, sr 96000, ch -1, bufsize -2352, bufno 2, req. latency 49 msec
Debug: PortAudio: getInterfaces()
Debug: Api name: OSS
Debug: /dev/dsp
Debug: name /dev/dsp, API 0, maxOutputChannels: 0
Debug: Api name: ALSA
Debug: HDA Intel: STAC92xx Analog (hw:0,0)
Debug: Api name: ALSA
Debug: default
Debug: Api name: ALSA
Debug: dmix
Debug: PortAudio: getInterfaces() end
Debug: PortAudio: getSampleRates()
Debug: m_devId: -1
Debug: PortAudio: getSampleRates() end
Debug: Api name: OSS
Debug: Api name: ALSA
Segmentation fault (core dumped)
```

---

### Post by ghindo on 2007-11-02
Bump

---

### Post by ghindo on 2007-11-04
Bump

---

### Post by ghindo on 2007-11-06
Bump

---

### Post by ghindo on 2007-11-09
Bump

---

### Post by ghindo on 2007-11-10
Bump

---

### Post by ghindo on 2007-11-11
Bump

---

### Post by ghindo on 2007-11-13
Bump.  Could someone at the very least point me to where I could find help for this issue?

---

### Post by ghindo on 2007-11-15
Bump.  Is there a problem with my video card?  Can it be fixed?

---

### Post by ghindo on 2007-11-19
Bump.

---

### Post by GameGod on 2007-11-20
Dude, when you have a problem like this and nobody's answering it, the best thing to do is go to the website of the software you have an issue with and file a bug or talk to the developers.

Go post a thread in the Mixxx forum or file a bug in the tracker:
[http://mixxx.sourceforge.net]("http://mixxx.sourceforge.net")

[http://sourceforge.net/tracker/?group_id=47577&atid=449891]("http://sourceforge.net/tracker/?group_id=47577&atid=449891")

(By luck, I do happen to be a Mixxx developer, but I don't check these forums that often, so please follow it up on our forum or in our bug tracker.)

---

### Post by patriot-xtx on 2008-06-07
rootDebug: If you have a Hercules device plugged into USB, you'll need to either execute 'sudo chmod o+rw- /dev/input/event?' or run mixxx as root

---

