---
title: "Bristol wont start -midi errors"
date: 2010-08-17
forum: Multimedia Software
---

### Post by jamespi on 2010-08-17
hi i'm a total noob when it comes to midi - i installed the bristol softsynth, but when i try to start it with "startBristol" i get the following errors:

```
startBristol -prophet
checking availability of TCP port 5028
using port 5028
generate bandwidth limited waveforms(31, 12)
spawning midi thread
could not reschedule thread
parent going into idle loop
Init waiting for midi thread OK status
Fixing samplerate at 44100
midi sequencer: bristol
Opened listening control socket: 5028
midiOpen: 5028(100)
Client ID = 129
Queue ID = 0
Registered 129 0
Device name "bristol" did not parse, defaults 128.0
Got midi thread OK status
bristol version 0.40.8
connected to :0.0
display is 2304 by 864 pixels
Window is w 2304, h 864, d 24, 0 0 0
Using DirectColor display
Initialise the prophet link to bristol: 83c2ea8
hostname is localhost, bristol
TCP port: 5028
Connected to the bristol control socket: 4
bristolengine already active
Accepted connection from 0 (3) onto 2 (5)
created 32 voices: allocated 32 to synth
	sid is 0
spawning audio thread
could not reschedule thread
init waiting for audio thread OK status
bristolAudioOpen(plughw:0,0, 44100, 256, 1a00008)
audioOpen(00120080, 0, 1024): plughw:0,0
opening device plughw:0,0, flags 0000000d
open playback on plughw:0,0, pre 8
Error opening PCM device plughw:0,0
Problem opening audio device plughw:0,0, exiting audio thread
Midi read retry (2150)
audio thread failed: exiting.
parent exiting
return - no data in buffer for 0
cleanupBrighton(0)
cleared sigpipe handler
cleanupBrighton(0)
midi write error, fd 4, size 1
return - no data in buffer for 0
socket closed
request acked: -1

```

i'm using lucid

any help would be appreciated
james

---

