---
title: "Sound Recording."
date: 2006-04-04
forum: Multimedia &amp; Video
---

### Post by kagashe on 2006-04-04
Hi,

Recently I installed Skype and my tryst with "sound recording" in Ubuntu Breezy began. I searched on this forum and did the following settings as suggested on one of the posts:
> System>Preferences>Sound
Uncheck Enable Sound Server Startup
System>Preferences>Multimedia System Selector
Set Default Sink to OSS Open Sound System
Set Default Source to OSS Open Sound System
I could not record sound from the external microphone.

I read number of posts in many threads with no result.

Then I went to [Skype Forum]("http://forum.skype.com") and serched for "Ubuntu" and found an excellent advice:
> For testing your audio-setup, I suggest you to use 
aplay -D default test.wav 
arecord -D default testrec.wav 
"aplay" and "arecord" are ALSA command line utilities. The first command did not play anything since there was no "test.wav" file.

But I could record from the microphone after using "arecord" command. Then I played the recording:
> aplay -D default testrec.wav

Then I found that I could also record from the "Sound Recorder" of Gnome.

After fiddling with some other "Sound and Video" programs I found that I could not record the sound once again. I restarted the PC and could record once again.

I found one excellent post [Unofficial Skype + Linux Sound FAQ ]("http://forum.skype.com/viewtopic.php?t=4489&highlight=ubuntu")on Skype Forum.

Hope it helps some people.

kagashe

---

