---
title: "Seriously, any way to increase max volume?"
date: 2008-08-18
forum: Multimedia Software
---

### Post by SomeGuyDude on 2008-08-18
Okay, I got a new pair of headphones and was curious to try 'em out. I, right now, have to have the volume set to 91% (with PCM maxed out) just to be loud enough to hear it clearly. Set at 100% it's not even close to being "too loud".

This isn't a new issue, either. My master volume always has to be sitting at around 85% if I plan on listening to things without my headphones in, and that's just to be sitting with my head two feet from the notebook speakers.

Back in Windows, I rarely had my volume over 50%. Now if a movie has a quiet part, even if the volume is maxed out I can't hear it. What gives, and how do I fix it??

---

### Post by Minipalmer on 2008-08-18
This was one of the first things I noticed when I got Ubuntu (about a week ago) and it is pretty annoying. I'd love some sort of code to just boost the max volume.

I tried showing a friend a video on my laptop speakers and the volume couldn't get loud enough for him to hear it while sitting next to me.

So here's to a free bump :)

---

### Post by trinoquad on 2008-08-18
Yeha@ I have the same problem. please if there is a quick solution let me know. Well it's my friend's computer, it had windows and the viruses killed it , so i decide to install Ubuntu, but the problem is the audio, is not loud enough , speaker don't ever make a sound. only headphones.

---

### Post by jsyl on 2008-08-18
Hey guys, I just found a way now. You have to go to the speaker icon at the top bar, and right-click it. Then choose "Open Volume Control". Then, put the Master, PCM, and Front bars all the way up. That should increase the volume by a lot.

---

### Post by Minipalmer on 2008-08-18
Mine are already all the way up lol.

---

### Post by s3a on 2008-08-18
Did anyone try to go in terminal type *alsamixer* then put everything to maximum?

---

### Post by markbuntu on 2008-08-18
What sound cards/chips are you guys using?
Have you tried using the Pulse Audio Volume Control?

This may be specific to some hardware because my sound gets as loud as I want.

---

### Post by SomeGuyDude on 2008-08-19
> **jsyl said:**
> Hey guys, I just found a way now. You have to go to the speaker icon at the top bar, and right-click it. Then choose "Open Volume Control". Then, put the Master, PCM, and Front bars all the way up. That should increase the volume by a lot.

First post:

> I, right now, have to have the volume set to 91% (with PCM maxed out) just to be loud enough to hear it clearly.

Not sure what card I have. Sound Blaster, I believe. And PulseAudio gives me this:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

---

### Post by Minipalmer on 2008-08-19
Typed in alsamixer and everything is maxed.

Card: HDA Intel
Chip: SigmaTel STAC9228

---

### Post by mocha on 2008-08-19
"HDA Intel" wow what a surprise..  Alsa 1.0.17 is supposed to fix the low volume issues as well as capture problems.  Installing the updated Alsa is fairly easy, there is even a script on this forum that someone wrote to automate it.  I submitted a bug report about Intel HDA and the old Alsa in Hardy and it got "triaged".

---

### Post by SomeGuyDude on 2008-08-19
> **mocha said:**
> "HDA Intel" wow what a surprise..  Alsa 1.0.17 is supposed to fix the low volume issues as well as capture problems.  Installing the updated Alsa is fairly easy, there is even a script on this forum that someone wrote to automate it.  I submitted a bug report about Intel HDA and the old Alsa in Hardy and it got "triaged".

The script worked just fine, but unfortunately I still need my volume at minimum 85% to listen to music. This is really weird.

---

### Post by Minipalmer on 2008-08-19
Hey guys found a fix that work for me:

> 
Originally posted by Sankz

I had a similar problem here...
Went to System >> Preferences >> Sound

Selecting Autodelect gave me this error:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Default Playback was 'Alsa' with device 'HDA Intel Alsa Mixer'
In Windows Xp I had 'Sigmatel Audio'

Changed it to 'OSS' with device 'Sigmatel STAC9211 A1 OSS Mixer'

Works like a dream... Get better volume as well as quality in Hardy now!


Found on this page:
[http://ge.ubuntuforums.com/showthread.php?t=799091](http://ge.ubuntuforums.com/showthread.php?t=799091)

---

### Post by Alistair George on 2008-08-22
Heres how I sorted it:
Under System/Preferemces/Main Sound and Video Menu make sure one of the last items Volume Control is checked then close Main Menu, go back to Sound and Video Menu section, open Volume Control and max Front (that was enough for me) but also, you could max PCM but that is probably an overkill.
Now I have same or more volume than in Windows.

If this fixes anybody elses issues please mark this thread as resolved thanks,
Alistair.

---

