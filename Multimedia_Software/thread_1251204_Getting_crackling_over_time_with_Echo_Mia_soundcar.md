---
title: "Getting crackling over time with Echo Mia soundcard - help please"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Rev2010 on 2009-08-27
I have an Echo Mia installed and working. I get sound fine but after a while a buildup of crackling ensues. Maybe around 10-15 minutes or so of playback. Now, I have the Alsa firmware and all that installed but I am using the Pulse audio mixer to control the volume as my speakers are studio monitors that stay at full volume - so I need to adjust the sound levels through keyboard hotkeys, and so far the only mixer that responds to the hotkeys is the Pulse. If I use the Alsa mixer I get sound but it's full blast. I haven't tested using the Alsa mixer over a period of time so I am unsure whether it's the Pulse mixer or something else.

Also, I can't figure out for the life of me where to change the audio buffer settings. I've installed the Echo Mia mixer but there are no options for buffer settings. Is there some .conf file I need to edit to change buffer settings? Anyhow, any help would be appreciated.


Rev.

---

### Post by Rev2010 on 2009-08-27
**Just a quick update:

I found some info online about editing the daemon.conf file. I changed the line:

; no-cpu-limit = no

to

; no-cpu-limit = yes

and (at the documents recommendation) the lines:

default-fragments = 8
default-fragment-size-msec = 10

to

default-fragments = 5
default-fragment-size-msec = 25

Been listening to music now for 47 minutes with no crackling. Hopefully that fixed it. I'm going to keep audio running for a while longer to see if the crackling continues.  I was surprised to see the CPU limit was on, so maybe changing that made a difference.


Rev.

---

### Post by Rev2010 on 2009-08-28
OK, I still get a little crackling but a lot less than before. But now I noticed my audio is mono!! Jesus this is getting so annoying. Why does there have to be so many different sound formats and why does it have to be so damn hard to get a soundcard to work correctly?? Honestly, it's no wonder why so few people use Linux. It really is quite frustrating.



Rev.

---

