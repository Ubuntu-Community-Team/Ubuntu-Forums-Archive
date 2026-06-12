---
title: "Recording audio over a telnet connection"
date: 2010-06-09
forum: Multimedia Software
---

### Post by npitts on 2010-06-09
Hello... I am going nuts trying to figure this out, any help would be appreciated.
 
I am using a PC to telnet into a Lucid Lynx Ubuntu system, and trying to record audio via a microphone which is connected to the Ubuntu system, and play it back on the PC. The microphone works when recording and playing directly on the Ubuntu system (so I know it's not hardware), but not when recording over the telnet connection. Playing other audio files does work over the telnet connection (so once again, I know it's not hardware), it's just the recording that doesn't work. 
 
So basically it's just the audio-in over the telnet connection that Ubuntu isn't liking. 
 
I tried removing PulseAudio (as I had a Fedora system that I had to do this with also, and that was the fix for that system), but apparently recording doesn't work at all in Ubuntu without it, as the microphone wouldn't work directly on the system anymore after in removed it. So I reinstalled it, but I am still stuck.
 
Any ideas? :confused:

---

### Post by rizzeh on 2010-06-09
wouldn't it be easier to do it **with** pulse audio? i thought that was the reason for introducing pulse audio - streaming audio from multiple sources including over network.

---

### Post by npitts on 2010-06-09
I'll do it with whatever works, using PulseAudio doesn't bother me, I only thought it was the issue because that was the case with the Fedora system. However, I got PulseAudio errors when running arecord on the Fedora system, but with this Ubuntu system, there are no errors whatsoever, it's just not recording anything at all. And it's not like it's just not picking up my voice, the file I am recording to is empty.

---

### Post by rizzeh on 2010-06-09
another idea: record audio on the server, then send the sound file over telnet, a simple script would do :)

---

### Post by npitts on 2010-06-09
Good idea, but I have to have it set up exactly the way I have it now, I can't use a server. :icon_frown:

---

### Post by cchhrriiss121212 on 2010-06-09
Have you used jack before? There is something called netjack that can do this.

---

### Post by npitts on 2010-06-09
> Have you used jack before? There is something called netjack that can do this.
 
Another good idea, I would like to be able to do this without any other apps. I think I should be able to do this without apps... maybe I'm wrong. If I cannot, I will be forced to use jack I suppose!

---

### Post by rizzeh on 2010-06-09
> **npitts said:**
> Good idea, but I have to have it set up exactly the way I have it now, I can't use a server. :icon_frown:

maybe i'm misunderstanding but you don't need to be at the server - issue record sound and send file commands over telnet.

---

### Post by npitts on 2010-06-09
> maybe i'm misunderstanding but you don't need to be at the server - issue record sound and send file commands over telnet. 
 
I have to record the sound on the Ubuntu system and play it back on the PC. Unfortunately, there's no way around that.

---

