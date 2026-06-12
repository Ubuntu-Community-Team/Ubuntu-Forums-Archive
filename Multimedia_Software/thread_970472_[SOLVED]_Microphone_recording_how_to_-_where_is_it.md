---
title: "[SOLVED] Microphone recording how to - where is it???"
date: 2008-11-04
forum: Multimedia Software
---

### Post by tiggsy on 2008-11-04
I had to reinstall from scratch so the hours i put in getting recording (from mic using any software you like, though last time it was just sound recorder) to work finally with the help of a really comprehensive guide on here have to be gone through again. But i can't find the guide. Anybody can give me a link?

Surely it should be a sticky guide.

---

### Post by markbuntu on 2008-11-04
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by tiggsy on 2008-11-05
Thank you, i had actually seen that.

That is useful if you aren't getting sound when you play music and so on. I've not got that problem, though i still read through it and tried a few things. But there's virtually nothing about enabling recording.

The guide I used last time was ALL about recording. That is the one i need.

---

### Post by markbuntu on 2008-11-06
If you have not looked in my guide lately, I added a **Testing Recording** section a few weeks ago but yes, it is still a little thin on the recording side of things which is something I would like to fix but in general if you follow the guide recording should work.

If you find that other guide, let me know and I will add a link in my guide.

---

### Post by tiggsy on 2008-11-07
I suspect it may have been lost. It was mainly about settings in the Volume Control thing as i recall.

I have it set to device Alsa mixer

In preferences, I have selected Master, Headphone, Tone, Bass, Treble, all the 3D control options, all the PCM options, Front, Surround, Center, LFE, Side, Side capture, Line-in, Line2, Line2 Capture, CD, Microphone, Microphone Capture, Mic Boost (+20db), PC Speaker, Aux, Aux2, Aux2 Capture, Audigy Analog/Digital Output Jack, Audigy CD, Audigy CD Capture and External Amplifier

I have 5 switches available: 

Tone (not selected)
3D Control (not selected)
Mic Boost (selected)
Audigy Digital/Analog Output Jack (selected)
External Amplifier (selected)

In the Recording tab i have the Microphone set on (not crossed out) and set to the loudest. In the Playback tab, i have the Microphone also set on.

In System->Preferences->Devices i have everything set to ALSA. 
Sound playback works fine, and the Tests produce a sound. 
Capture Test looks good, but there's no sound.

The Recording Level Monitor shows nothing if i blow at the mic. I can't have it open at same time as Sound Recorder (what is the point of that?), but when i record anything on Sound Recorder, playback reveals nothing has been recorded.

The mic is still plugged into the same hole it was in before I had to change boot drives, it worked before.

---

### Post by tiggsy on 2008-11-07
I went back to your instructions, found "Testing, Recording" and set sound preferences - devices - Sound capture to PulseAudio

Then i clicked Test and got:
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused

To be honest, i dont see what pulse audio is for. I'm perfectly to go with the standard stuff instead, as i do want to use audacity. But the most important thing is to actually be able to record from mic.

---

### Post by markbuntu on 2008-11-07
Specifically with the audigy and audigy based cards if you have the Analog/Digital switch selected, you will be unable to record as the mic capture will be sent to the digital output. This has been reported by many users of audigy cards.

---

### Post by tiggsy on 2008-11-08
i unchecked the switch and tried again, no joy

I went into the preferences and deselected it, tried again, no joy

Then i rebooted, still no joy

I have 24-bit Soundblaster card

NOTE: after unchecking that, i had no sound, so i have had to recheck it.

---

### Post by tiggsy on 2008-11-25
I figured out why the mic wasn't working - my kitten had chewed through the wire. After i got my new mic this morning, it's working fine.

Doh.

---

