---
title: "LFE Remixing in Pulseaudio default to Off constantly."
date: 2010-04-12
forum: Multimedia Software
---

### Post by xanmalone on 2010-04-12
After installing the PulseAudio Volume Manager i've noticed that the LFE was completely silent.

After a bit of digging i've found out that for some bizarre reason they turned LFE mixing off. I've reenabled it and it now "works".

First off, a restart didn't do the job. LFE wasn't being used at all until i manually changed the Internal Audio profile from 5.1 to anything and back. As soon as you select or switch to anything the LFE mixing goes into effect.

And now, everytime you stop listening to music or whatever application that might need to play sound, the LFE mixing goes dead until you manually reselect a Internal Profile. With something like VLC this will turn off after every MP3, which turns the sound quality into subquality mush.

Any idea why this might be happening? I've seen a bugtrack on a very similar issue, but no idea if anybody found a solution.

---

### Post by quequotion on 2010-04-12
> **xanmalone said:**
> After installing the PulseAudio Volume Manager i've noticed that the LFE was completely silent.

After a bit of digging i've found out that for some bizarre reason they turned LFE mixing off. I've reenabled it and it now "works".

First off, a restart didn't do the job. LFE wasn't being used at all until i manually changed the Internal Audio profile from 5.1 to anything and back. As soon as you select or switch to anything the LFE mixing goes into effect.

And now, everytime you stop listening to music or whatever application that might need to play sound, the LFE mixing goes dead until you manually reselect a Internal Profile. With something like VLC this will turn off after every MP3, which turns the sound quality into subquality mush.

Any idea why this might be happening? I've seen a bugtrack on a very similar issue, but no idea if anybody found a solution.

Perhaps our problems are related somehow? [ Surround Sound in Karmic with Pulseaudio ](http://en.ubuntuforums.org/showthread.php?t=1452473)

How about your rear-left and rear-right? are they almost or completely silent as well?

---

### Post by xanmalone on 2010-04-18
> **quequotion said:**
> Perhaps our problems are related somehow? [ Surround Sound in Karmic with Pulseaudio ]("http://en.ubuntuforums.org/showthread.php?t=1452473")

How about your rear-left and rear-right? are they almost or completely silent as well?

My rear sound components work fine, but the Low Frequency Graph gets nothing at all. It's a real shame, if our problems didn't exist.. The sound would be perfect nearly

---

### Post by Yellow Pasque on 2010-04-18
```
gksu gedit /etc/pulse/daemon.conf
```
Find this line:
```
; enable-lfe-remixing = no
```
Change to:
```
enable-lfe-remixing = yes
```

---

### Post by xanmalone on 2010-04-26
> **Temüjin said:**
> ```
gksu gedit /etc/pulse/daemon.conf
```Find this line:
```
; enable-lfe-remixing = no
```Change to:
```
enable-lfe-remixing = yes
```

Was already turned to yes as per first post

---

### Post by quequotion on 2010-06-10
> **xanmalone said:**
> Was already turned to yes as per first post

Same here.

Also, I've found the rear speakers work when playing a video encoded with actual surround sound audio, although I don't have any good clips to test how loud they could get.

I occasionally hear muffled clicking (with my ear right against the speaker) from the subwoofer when playing a video encoded with surround sound audio, but no tones or perceptible audio. Does it need to be amped?

---

