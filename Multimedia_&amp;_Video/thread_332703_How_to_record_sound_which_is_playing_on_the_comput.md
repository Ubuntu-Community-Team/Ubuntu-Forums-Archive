---
title: "How to record sound which is playing on the computer?"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Starlight on 2007-01-06
Hi! I have a question... if I'm playing some sound in Ubuntu, how can I record it at the same time (in the way that what's playing on the speakers is also recorded into a sound file at the same time)?

---

### Post by Biggus on 2007-01-06
This solution is maybe a little basic for what you require, but I've used a little program called 'Sound Recorder', which I found in my 'Applications->Sound & Video' folder.

I might well have installed it from the Synaptic Package Manager in 'System->Administration', or it might have came as default with my install, I really cant recall.

I only want to record short clips, and it seems to work OK.

---

### Post by Starlight on 2007-01-06
Hi! Thanks for the reply... but I tried that, and it didn't work. I have a program called "KRec Recording Tool" (I recently switched to Kubuntu), but it records empty files that way... I also installed KWave, but when a sound is playing and I try to use the record option, it says that the sound card is in use...

---

### Post by Biggus on 2007-01-06
Yeah, I had a few hassles with it as well (I still don't know what a MUX is), I simply messed around with it until I got it to play a sound.

I used to get 'soundcard in use' issues when I used doze (WMP refused to play), but never in ubuntu yet.

Maybe there is some sort of way to kill all processes which are using the soundcard?

(I'm guessing that it's gonna involve the terminal at some point)

---

### Post by Starlight on 2007-01-06
well... the problem is that there is a process that is using the soundcard... and I want to record what that process is playing...

---

### Post by Starlight on 2007-01-06
I found an online guide about how to do it, and it says to use a program called Audacity. So I downloaded it... the guide said to pick "Wave Out Mix" as the audio recording device.... the problem is that there's no "Wave Out Mix" on my computer! :( I only have: Vol, Line, Mic, CD, Line1, PhoneIn, PhoneOut, and Video...

EDIT: It doesn't matter which one of these I choose, I get an "error while opening sound device" when I try to record anything while another program is playing something :(

EDIT 2: It seems that disabling the sound system in KDE fixed it! I finally can record stuff... the quality is very bad, but maybe I'll find a way to improve it :D

---

### Post by Rob_H on 2007-01-06
You have to tell Audacity to "share" the sound card with other applications. Try invoking it like this:

```
aoss audacity
```

This forces Audacity to access the sound card through the ALSA layer. Note that you might have the same issue on whatever application is generating the sound. It depends on whether or not it was written with built-in support for ALSA or a sound server. If not, you can trick it in some cases by using a wrapper like "aoss" (shown above) or "artsdsp".

You might also need to configure your sound card for "full duplex" operation, assuming it supports it. If you're using Kubuntu, you'll find this in the Sound System Settings. 

Having said all that, I have tried doing what you're doing, and haven't gotten it to work either. I think it's a limitation of my sound card or driver.

Of course, you could also try plugging in a wire from "line out" to "line in".

---

### Post by macabro22 on 2007-07-06
Thanks!!!

---

### Post by stmiller on 2007-07-06
Jack (audio connection kit) can record internally. In fact, that is what it is used for, among other things. You can record from Rosegarden output into Audacity, for instance, internally. But is slightly complicated to setup at first.

sudo apt-get install qjackctl

---

