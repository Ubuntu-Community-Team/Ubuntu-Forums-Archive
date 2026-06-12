---
title: "Help with Skype"
date: 2010-07-19
forum: Multimedia Software
---

### Post by minty fresh taste on 2010-07-19
I'm having issues with Skype

I'm running Linux Mint 9
have a Logitech Premium Stereo 350 headset
Pulse Audio

I can't seem to get the audio to play in the headset
(speakers only)
Mic works fine

I feel I've tried every combination
of pulse/Skype settings 

Please advise...

---

### Post by valbaca on 2010-07-19
Is the sound only not working in skype? Can you get audio to play in your headset from, say, audio files or websites?
 
If you cannot get audio from any other sources, it may not be a Skype-specific problem.
Check your audio output settings:
Click on the sound icon in the panel and go to Sound Preferences (it may be Sound Properties, I'm not on my Ubuntu box right now). From there you can mess with settings and drop-down menus to find what works.
 
This is how I got my Xbox/PS3/PC gaming headset to work (mine uses a regular audio jack for input audio and uses the USB for the mic and power.

---

### Post by minty fresh taste on 2010-07-19
I can switch in sound properties so the sound
comes out headphones or speakers
on my old windows box
skype would come thru headphones
without affecting audio out of speakers

---

### Post by kostkon on 2010-07-19
Install the *PulseAudio Volume Control* utility. It will allow you to set your headset as the input and output device for Skype (open the volume control utility, start Skype and you'll see its streams in the *Playback* and *Recording* tabs). Your other sounds will continue to play through your speakers.

You only need to do this once; pulseaudio will remember your choice.

---

### Post by minty fresh taste on 2010-07-19
I've got the pulse audio control installed
when skype is running
i simply see no mention of it in
the pulse volume control window......
It's making me crazy!

---

### Post by kostkon on 2010-07-19
Do you have the latest version of Skype?

---

### Post by minty fresh taste on 2010-07-19
just built my mint box 1 week ago
and am using the skype beta from
software manger

---

### Post by Ready2DropWin on 2010-07-19
I got my version of skype from their website, and I have no issues with it. You may wan to try that.

---

### Post by minty fresh taste on 2010-07-19
From within Skype settings
sound devices
Microphone
and speakers the only choice from the drop-down
is PulseAudio server 
should it not give me the choice of my logitech headset?

---

### Post by minty fresh taste on 2010-07-19
**FIXED**
removed pulse audio
and installed alsa
works like a charm

---

### Post by valbaca on 2010-07-20
> **minty fresh taste said:**
> **FIXED**
removed pulse audio
and installed alsa
works like a charm
 
Good to hear! and to know for future reference.
Please mark thread as [Solved]

---

### Post by minty fresh taste on 2010-07-20
new to the forum...
how do I do that?

---

### Post by valbaca on 2010-07-20
In the top right, there is a drop down menu called "Thread Tools" with a "Mark as solved" option.

---

