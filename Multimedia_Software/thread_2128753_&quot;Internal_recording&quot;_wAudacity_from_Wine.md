---
title: "&quot;Internal recording&quot; w/Audacity from Wine application (RehearScore)"
date: 2013-03-24
forum: Multimedia Software
---

### Post by paulvbrown on 2013-03-24
Hey all.

I'm running Ubuntu 11.10 on a FujitsuSiemens Amilo something something...

In order to get RehearScore to install, I had to go to winetricks, select default wineprefix, change settings, and check sound=alsa.

That let me run the RehearScore installation using wine.

In a terminal, b4 I start up RehearScore, I run "timidity -iA", which starts timidity w/"Alsa sequencer interface".

So when I start up RehearScore, I have sound.  So far so good.

NOW the problem:  I'd like to record this playback w/Audacity.  I've tried the "simple" version of just plugging my headphones straight into my microphone, but that resulted in a crackly, non-acceptable recording.

Since then I've tried a couple of solutions I've found off the internet, but none of them have taken.  These include using pavucontrol and simply setting the output settings in the normal Ubuntu sound settings.  I'm thinking that perhaps the RehearScore / Wine / Timidity / MIDI -combination is the source of the trouble.  REALLY need someone who understands how all these sounds get routed to and fro to figure this one out (and preferably explain it, so I'd maybe understand what I'm doing in the future and not just blindly following instructions, but naturally I'm happy for some copy-paste instructions from anyone as well.

THANKS in advance...

---

### Post by robert shearer on 2013-03-24
One possible solution would be to have audio-recorder running as it will record anything currently using your soundcard, in other words if you can hear it then audio-recorder can record it.
Multiple options for output format and simple to use.

[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
[http://handytutorial.com/install-audio-recorder-in-ubuntu-12-10-12-04-using-ppa/](http://handytutorial.com/install-audio-recorder-in-ubuntu-12-10-12-04-using-ppa/)

---

### Post by paulvbrown on 2013-03-26
Robert - thanks, I'll give it a try.  Meant to do it last nite, but spaced it AND ran out of time.

---

### Post by paulvbrown on 2013-04-07
Argh. Ok, finally got around to trying this...

option 1) I start timidity (timidity -iA), start RehearScore, then audio-recorder.  I start a song in RehearScore, and can hear it.  I press StartRecording in audio-recorder, and nothing happens.

option 2) I start timidity, then start audio-recorder, then start RehearScore.  NOW when I press StartRecording in audio-recorder it seems be working, but now when I start the song in RehearScore nothing can be heard, and no sound is recorded.  The terminal where I have started timidity has a couple of lines: Can't open pcm device 'default'. and Couldn't open ALSA pcm device (`s')

I can start things up in the same order as in option 2, and start the song in RehearScore BEFORE trying to start recording, then again, I can hear the song, but actual recording isn't possible...

---

### Post by paulvbrown on 2013-04-07
Hey!

Well, of course I should have ALSO tried a restart, which magically seemed to solve the problem...  THANKS again!

---

