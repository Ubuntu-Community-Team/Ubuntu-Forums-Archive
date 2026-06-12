---
title: "Simple Microphone Program"
date: 2010-04-17
forum: Multimedia Software
---

### Post by monsieurdozier on 2010-04-17
I need a simple program that I can talk into a microphone and the sound will come out the speakers.  I want to use my Computer that's hooked up to the store speakers as a PA System.

I am having a difficult time finding a program that will let me do this without having to record and playback.  Any help would be wonderful.

Thanks.

---

### Post by RTrev on 2010-04-17
> **monsieurdozier said:**
> I need a simple program that I can talk into a microphone and the sound will come out the speakers.  I want to use my Computer that's hooked up to the store speakers as a PA System.

I am having a difficult time finding a program that will let me do this without having to record and playback.  Any help would be wonderful.

Thanks.

My first thought was that maybe there's some software of the sort a DJ would use while playing music, talking to the crowd, and so on.  A quick search turned up this thread:

[http://ubuntuforums.org/showthread.php?t=824646](http://ubuntuforums.org/showthread.php?t=824646)

Hope this helps, or at least gets you onto the right track.

---

### Post by monsieurdozier on 2010-04-17
I tried the DJ software in the repositories, and couldn't find really what I was looking for.

Then I found this thread: [http://ubuntuforums.org/showthread.php?p=8672035](http://ubuntuforums.org/showthread.php?p=8672035)

But I'm having the same problem with the delay.

I'll keep looking, thanks for your help!

---

### Post by RTrev on 2010-04-17
Okay, this may be a crazy idea, or perhaps I'm doing it in a less than optimal way, but I tried this:

```
arecord | aplay
```

Do a Ctrl/C to stop it.

And yep, I get microphone output from the speakers.  It generated some errors at the console, but just maybe this idea can be cleaned up by someone more knowledgeable than I.

Worth a try anyway. <g>

---

### Post by gordintoronto on 2010-04-17
You don't need a program. As soon as I un-mute my microphone, I hear my breathing in my earphones.

---

### Post by RTrev on 2010-04-17
> **gordintoronto said:**
> You don't need a program. As soon as I un-mute my microphone, I hear my breathing in my earphones.

Yeah, I just Googled this and people are asking how to *avoid* having their microphone go straight to the speakers.  The advice is always to go into their sound mixer and play with the mute/unmute controls.

---

### Post by monsieurdozier on 2010-04-17
I'm not sure, for me it doesn't work by default.

I tried the two commands in this thread, and they both work, unfortunately with a delay.

I appreciate the help.

---

