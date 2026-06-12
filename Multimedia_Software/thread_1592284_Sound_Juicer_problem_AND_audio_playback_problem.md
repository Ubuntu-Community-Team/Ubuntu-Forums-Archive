---
title: "Sound Juicer problem AND audio playback problem"
date: 2010-10-10
forum: Multimedia Software
---

### Post by ghdvfddzgzdzg on 2010-10-10
I've got two problems. I hope it's OK to post them together instead of making two threads, and I suppose they could be related.

1. I'm using Sound Juicer to rip mp3s. I found I was able to rip OK, but with no ID3 tags. I added 

! id3mux

to add tags. That didn't work, so I swapped that out for 

! id3v2mux

but that didn't work. Somehow, now, even if I remove the nonfunctional tag, Sound Juicer just hangs. I've tried ripping with a number of audio profiles, including original presets like "CD Quality, MP3," and none of the ones I've tried will rip.

I tried removing Sound Juicer, and when I reinstall it, it still has my presets and everything, so maybe I need to do a command line uninstall and not a Software Center removal. Could that help?

I don't know if it's related, but Sound Juicer now says "Retrieving track listing...please wait" indefinitely. I didn't notice if it said that before though. Any ideas how to a., get ripping back, and b., how to add id3 tags successfully?

PROBLEM 2

I have audio conflicts. Amarok and other audio sources cannot play audio simultaneously. I've tried a few fixes around but nothing has worked. The details:

If I'm playing music in Amarok (or even if Amarok is paused) my Chrome browser plays a soundless Youtube video. 

If Chrome had Google Chat or Youtube open, and they made sound, Amarok then will not play sound, and it gives me an error—one that I can't get it to give me now, how weird, but it did this morning—telling me that it's switching sound drivers to the digital one (from the analog one), though no sound is coming out. I have to restart Amarok (which never really closes if this happens; I have to kill its processes before restarting it) to get sound out of it again. 


I think this is probably an ALSA vs. Pulse problem, but I tried to install Pulse and could not get it to install. Could that be problem? Either way, this is annoying. Any ideas here? Thanks, folks.

---

