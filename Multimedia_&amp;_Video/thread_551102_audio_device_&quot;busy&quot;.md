---
title: "audio device &quot;busy&quot;"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by cypher35 on 2007-09-14
I have got a problem with the command-line "play" command (part of the sox library).

When run by itself, it works just as it should, however if I have amarok or kaffeine running with audio, the play command fails with the following message:

```
mike@Scud:~$ play ~/.sfx/volume.aiff
sox: Can't open output file '/dev/dsp': Device or resource busy

```


It cannot simply be an issue with multiple devices using the sound card at once, because both kaffeine and amarok seem to share it nicely.

I recently replaced my motherboard with a different one (which has a different on-board sound device) and then re-installed kubuntu, but this command worked just fine on my last installation (which had the same setup otherwise).  I am running AMD64 Kubuntu Feisty.

Please advise.
-Mike

---

### Post by deadgobby on 2007-09-14
So if you just run the on board sound device and if you closed out the program that is using sound. Then you get that error. You need to open up the terminal and type in

kill all esd

If you run a 64 bit kernel may be a cause to that little bug. 

Gobby

---

### Post by cypher35 on 2007-09-14
No, the problem doesn't persist after I've quit out of the program currently using the audio device...

If amarok and kaffeine are not running, the play command works just fine.  It's only when another application is playing audio of some sort that I get this "device is busy" error.

---

### Post by thirdspace on 2008-03-14
Congratulations, you have found a symptom of one of the oldest still-not-fixed really stupid bugs in all of Linux-land. Depending on the audio hardware you have, multiple programs directly opening and writing to the audio device may or may not work. Probably it won't work, and you get a "device is busy" error, which some programs, by the way, just ignore and either hang or run "silently". It turns out there are an incredible number of different ways for programs to indirectly open a sound device, and for some of these ways, the indirection allows the sound device to in effect be shared. "play" happens to be a very old command that uses a deprecated interface to the sound device that doesn't share very well.

If you install the alsa-oss package and type "aoss play whatever.wav" instead of just "play whatever.wav" the sound gets routed a different way and just might be allowed through.

---

