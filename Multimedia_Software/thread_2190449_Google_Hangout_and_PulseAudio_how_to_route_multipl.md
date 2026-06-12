---
title: "Google Hangout and PulseAudio: how to route multiple audio sources as Hangout input?"
date: 2013-11-27
forum: Multimedia Software
---

### Post by marcozambi on 2013-11-27
What I would like to achieve is the capability to provide Google Hangout with an audio input virtual device that is the result of a merge between different audio sources. 

In the simplest case the situation would be:
[LIST]
[*]Source 1: USB or Internal microphone
[*]Source 2: Any audio software source (VLC,mplayer,etc.) playing some audio.
[/LIST]
As said, Source 1 and 2 should be merged to a virtual input device, "detectable" from Hangout among the available input sources.

I think it's easy to performe the merge of the 2 sources in a null sink with PulseAudio: basically I'll have to create 2 loopback and 1 null sink loading the relevant modules.
What I do not get is:

[list]
[*]Is it possible to create a virtual input device with PulseAudio?
[*]If possible, how should I connect the null sink to the virtual input device?
[/LIST]

I think this could be really useful for all the people having a live Hangout and willing to mix voices with audio files...
Thanks in advance!

---

### Post by tgalati4 on 2013-11-27
These may help get you closer to what you want:

[http://superuser.com/questions/552788/alsa-pulseaudio-mixing-output-from-multiple-processes](http://superuser.com/questions/552788/alsa-pulseaudio-mixing-output-from-multiple-processes)

[http://unix.stackexchange.com/questions/34526/how-to-change-mixing-of-channels-by-pulse-audio-alsa](http://unix.stackexchange.com/questions/34526/how-to-change-mixing-of-channels-by-pulse-audio-alsa)

Send an email to the google hangout develepers and see if they have any ideas.

Also, there is a forum for hangouts.  Perhaps asking here as well:  [http://productforums.google.com/forum/#!categories/hangouts](http://productforums.google.com/forum/#!categories/hangouts)

---

