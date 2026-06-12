---
title: "Sound &quot;mutes&quot;"
date: 2009-11-08
forum: Multimedia Software
---

### Post by kongstad on 2009-11-08
I made the mistake of upgrading to 9.10 during beta, so I don't know if that is the root of my problems.

I guess my best bet is to make a clean install of 9.04 which was rock solid.

Well after days of work my computer boots again, the power button works, and the wi-fi is usable, with only about 5-10% downtime.

So now I've started to focus on the smaller issues.

In 9.04, the headphone port did not mute the internal speakers. I discovered that double clicking the volume thingie muted the sound, but not the headphones (I use the headphone port to connect to the stereo). So I was happy.

The good news with 9.10 is that when I plug in the headphone jack, the sound mutes. The bad news is that all sound mutes.

Unlike 9.04, double clicking does nothing, so I have to right click, select mute, which then marks the sound as muted, the right click again to unmute to get sound through the headphone.

This however turns on the internal speakers. To mute them I have to change the audio output to "Analog headphones".

Thats not all. I originally thought that it was the action of connecting a jack that caused the muting of all sound, but now it seems to mute whenever I close whatever player I am using.

For example. I am watching a youtube video in firefox. To get sound on internal speakers I mute then unmute. I close the frame. Open a new frame, go to the same youtube video (any), and the sound is of. I have to mute it, and unmute it to get it back.

I am using vanilla settings for sound
My sound device seems to be:
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
	Subsystem: Inventec Corporation Device [1170:0040]


I use Alsa.

Are these general problems, or is it my Zepto 6625WD, that is getting to old?

---

### Post by kongstad on 2009-11-10
I solved the problem by using this solution:
[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

I have a zepto 6625WD so I started by adding the line

options snd-hda-intel probe_mask=1 model=[COLOR=DarkGreen][B]zepto[COLOR=Black]

[/COLOR][/B][COLOR=Black]since my sound system is alc268.

This however disabled my headphone. I then tried 

[/COLOR][/COLOR]options snd-hda-intel probe_mask=1 model=[COLOR=DarkGreen]**auto**[COLOR=Black]

Which did the trick. The internal speakers mute when I insert the headphones, and music keeps playing in the headphones. Furthermore the sound is on when I start the computer!


[/COLOR][/COLOR]

---

