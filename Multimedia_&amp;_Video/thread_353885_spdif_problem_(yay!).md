---
title: "spdif problem (yay!)"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by mabris on 2007-02-05
I'm trying to set up spdif sound on Edgy.  THe analog sound works fine.  I can only get spdif sound in three places:

the login screen: login sounds and error beeps if i type in the wrong password
banshee: i can play mp3s in banshee, but no where else
the test sound in sound preferences

No other mp3 players work (i've tried them all!) and I can't find  a player that plays the sound in video files.  Playing system sounds in sound preferences doesn't work either.

My settings:

aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

.asoundrc (both in home folder and /etc) I've tried having only in one, and also naming as asound.conf), from another forum thread.

pcm.!default {
type plug
slave.pcm "dmixer"
}


pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,2"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
bindings {
0 0
1 1

IN sound preferences I have all playback devices set to NVidia CK85 IEC958.  No other choices give me the test sound or sound playback in banshee.

Any clues as to what's going on?

---

### Post by mabris on 2007-02-05
Update: DVD audio (but no other) plays in Xine with passthrough selected.

---

### Post by mabris on 2007-02-05
OK, problem solved.  I ended up not having the .asoundrc in my home (misunderstood what was meant by home).

cp /etc/.asoundrc /home/*username*/.asoundrc fixed it for me

---

