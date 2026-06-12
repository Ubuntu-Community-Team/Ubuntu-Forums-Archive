---
title: "Alsa &amp; alsa-jack-plugin =&gt; JACK isnt work"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by HellMind on 2007-10-27
I want to know if someone is using alsa and jack at same time

I need jack to play my midi keyboard

And alse for the rest, games mp3 videos

I Compiled and installed the alsa jack plugin because it was missing (long ago)

But i cant use any aplication when jack is on, because that resource is getting busy

But with ETQW it tries to use jack but i got this error

opened Alsa PCM device default for playback
SND_PCM_FORMAT_S16_LE failed: Invalid argument
close pcm
dlclose

why?
should I use jack only :(?

How can i replace alsa with jack?

---

### Post by lunar_shuttle on 2008-03-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/148510](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/148510) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Did you ever get this one working? I just upgraded to Gutsy and have been banging my head against the wall for a couple of hours now.... Seems  [there is a bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/148510") in libasound2. This used to work like a charm in feisty, and apparently there's a fix for it in debian.. :(

I've rebuilt and reinstalled it but asound still won't play. I only get the:

aplay: set_params:900: Sample format non available

---

