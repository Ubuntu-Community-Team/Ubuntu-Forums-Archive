---
title: "[SOLVED] can play but can't record"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by cincinnatus on 2007-05-28
I'm trying to record some line-in audio via cassette tape.

The audio plays on the speakers, but does not record in Audacity or Sound Recorder.

The "Recording Level" app shows activity, but the Audacity "Meter Toolbar" doesn't.

I want to be able to tell Audacity what type of input device to use, but the little drop-down menu isn't there like it is on windows, and according to [this thread]("http://audacityteam.org/forum/thread/490") it's not supposed to be there on the newer version of audacity for linux - I'm supposed to do something with the Alsamixer.

So I fiddled with the Alsamixer, but I don't really know what I'm doing, and it's not helping.

After I fiddled with Alsamixer a bit, and then tried to record with Audacity, I got this error message:

> Error while opening sound device. Please check the input device settings and the project sample rate.

I don't know how to check the input device settings and the project sample rate!

Thanks in advance for your help.

EDIT:

I should also mention that I had managed to get the microphone working on Audacity, and could record with it.

It doesn't work now, though. When I set the Alsamixer switch to microphone, it does the same thing as the line-in does, and gets the same error message as Audacity.


Tell me how to fix it.

---

### Post by cincinnatus on 2007-05-28
Okay, I fixed it myself. Looks like lots of people are having all sorts of problems recording sound in ubuntu. I posted this thread because it looked like no one had my exact problem.

But I looked at [this thread]("http://ubuntuforums.org/showthread.php?t=102377"), and saw what Oceola said:

> I have an older Ensonic Card 1371, the Device manager identifies pretty near all the functions and I can either record using the "Sound Recorder" or use "Audacity."
In order to use Audacity I have to go to /System/Preferences/Sound/ and uncheck the block marked "Enable sound server startup", in order to return the system sounds I just recheck it after I've done with the Audacity Session.

So I did that exact thing, and also made sure that the switch in the alsamixer (volume control) was set to line-in and not microphone, and now it works fine.

I hope this helps anyone with the same problem.

---

