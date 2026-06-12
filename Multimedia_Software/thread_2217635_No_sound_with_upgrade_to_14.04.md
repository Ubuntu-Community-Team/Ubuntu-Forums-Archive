---
title: "No sound with upgrade to 14.04"
date: 2014-04-18
forum: Multimedia Software
---

### Post by agemini68 on 2014-04-18
My sound is out since I upgraded from 12.04 to 14.04. I already checked mute settings and went into alsamixer to make sure the right sound card is selected and when I check settings in sound, it still displays dummy output instead of stereo duplex. I have an integraded sound card. Any suggestions?

I got it, install Pulseaudio preferences from the software center, run it once installed, on the tabs at the top, go into Multicast/RTP,, check enable multitask rtp receiver, enable multitask rtp sender, check send audio from local speakers. That did it for me, hope this helps someone else.

---

### Post by kevn57 on 2014-04-18
Thanks that worked for me as well

---

### Post by agemini68 on 2014-04-19
I spoke too soon, when I came home, I restarted the computer and the sound was out, redid all the settings and still no sound, uggh!

---

### Post by Ubi_one_2014 on 2014-04-19
what kernel do you run?

uname -r [enter] in a terminal

---

### Post by agemini68 on 2014-04-20
3.13.0-24-generic

---

### Post by agemini68 on 2014-04-21
I went and got a brand new soundcard, I have sound, but only in the left speaker.

---

### Post by mörgæs on 2014-04-21
How does it work in a live boot?

---

### Post by agemini68 on 2014-04-22
Same thing, sound in only the left speaker

---

### Post by mörgæs on 2014-04-22
It could be a bug which needs reporting, but first I think we should move the thread to Multimedia to see if anyone there has a good idea.

---

### Post by agemini68 on 2014-04-23
This is not a bug, I know about alsamixer, and my mouse worked on some things, so when it didn't select the other bars, I didn't think to try the arrow keys.#-oHere is simple step by step solution

1. In the terminal, type alsamixer
2. Select your soundcard (press F6), mine was CA0106.
3. Look for stereo items with one channel muted (text beneath bars looks like "63<>0").
4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C) [I have arrow keys]
5. Exit (ESC), no need to save manually.

---

### Post by mörgæs on 2014-04-23
Thanks for posting. Please add to the [workaround]("http://ubuntuforums.org/showthread.php?t=2217536") thread.

---

### Post by agemini68 on 2014-04-23
Just an FYI this is to fix the sound in left speaker only for the soundblaster audigy se soundcard. I never solved the no sound issue with my built in audio.

---

