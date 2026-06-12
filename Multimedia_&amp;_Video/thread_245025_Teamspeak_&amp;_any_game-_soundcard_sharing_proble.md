---
title: "Teamspeak &amp; any game- soundcard sharing problem"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by morton on 2006-08-27
I am having problems with sound in ubuntu. The problem is: when I want to run teamspeak and et in the same time I have no sound in et.

Normally, when I run them separately, they work flawlessly. Before I run ET I have to run:

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

in order to have sound in game. But even with these commands I cannot run TS and ET at the same time. I use the newest alsa drivers. ET and TS both use oss (atleast I think so...) so when I run ET this is what I get in the console:

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp

Now, I have tried running ts with aoss, but it doesn't seem to work (both playback and capture are disabled in ts then)- same thing happens if i run et with aoss (no sound in et). The sound card which i use is Sound Blaster Audigy LS. I have completely no problems with running ET + TS under windows. I must say that its pretty strange that an ubuntu doesn't support many processes sharing a sound card :confused: I wouldn't like to install windows again, so thats why I ask if anyone has a solution to this problem.

---

### Post by encompass on 2006-08-27
Talk to alsa... they have great support.  They helped me many times.
When you figure it out... don't forget to post your fix here.

---

### Post by morton on 2006-08-27
How should i contact them? Using bug reporting system on their site or do they have any forum (haven't found any on google)?

---

### Post by encompass on 2006-08-27
Just type alsa in the address bar of firefox or click here...
[http://www.alsa-project.org/](http://www.alsa-project.org/)
Search for the problem... them submit the bug.

---

