---
title: "low audio output"
date: 2008-09-04
forum: Mythbuntu
---

### Post by mark467 on 2008-09-04
why is the audio from tv and dvd so low on all my mythbuntu boxes and mp3 are really loud. i am constantly having to turn my volume up and down when switching back and forth. is there a way to correct this

---

### Post by Archmage on 2008-09-05
Did you incresse the volum within Mythtv? I think F11 or F12 is the correct key.

---

### Post by mark467 on 2008-09-05
that makes everything louder. my problem is mp3's are a lot louder than tv & Movies when i switch back and forth without changing volume

---

### Post by newlinux on 2008-09-05
Can you describe you audio setup (analog out, spdif passthrough, to audio receiver or TV speakers, etc.)? There are a lot of different variables, and in many cases the source files have different audio levels (it's really annoying when I am watching a station live and then it goes to commercial. The commercials are almost always noticeably louder than the show).

Also you may want to try changing volume levels of different controls in alsamixer.

---

### Post by mark467 on 2008-09-05
Ok my forntend has basic onboard audio (analog out to tv via 1/8 mini to rca) and my frontend/backend has a SB64 card (analog out via 1/8 mini to rca to surround sound amp) the both have the same issue. When playing tv recordings or dvd's i have to turn the tv or srs amp way up almost to max, mp3 are loud enough at normal listening lvls.
Example on fe w/ tv:  reg cable tv vol 13, regular dvd player vol 13, fe mp3 vol 13, fe dvd or recorded tv vol 38

At first i thought it was line in vol for recording tv but it does it with dvd iso's also. If I max out the line in it is still not as loud but gets distorted from to much gain.

---

### Post by newlinux on 2008-09-05
Hmmm.. Do you have the same problem if you play your recordings/dvd outside of myth with mplayer or VLC? This may help determine if it is the source or myth or...

How do you record your tv signals (what type of signal are you capturing/tuning)?

---

### Post by Crash87ss on 2008-09-18
I just noticed a similar problem on a new myth set-up, I'm not sure about mp3's being louder, but I need to have my reciever up very near max to get resonable volume. 

Right now I'm using onboard sound, analog stereo 1/8" to RCA to my reciever. Defaults setting in myth, except volume up to "90".
Sound is coming from a Biostar AM2 MB, nforce chipset. 

I will investigate the sound level at other times and post later. I also want to see if running digital over analog makes a difference, but it might be the weekend before I get to that.

---

### Post by mark467 on 2008-10-05
anyone have any ideas on this. as stated above...

audio receiver volume needs to be up really high for videos and recordings to be heard.
mp3's play at a normal lvl like all my other equipment. 

1/8th mini to rca for audio (sony surround receiver)

in alsamixer all the bars are set to 90's

---

### Post by agamotto on 2008-10-08
> **mark467 said:**
> anyone have any ideas on this. as stated above...

audio receiver volume needs to be up really high for videos and recordings to be heard.
mp3's play at a normal lvl like all my other equipment. 

1/8th mini to rca for audio (sony surround receiver)

in alsamixer all the bars are set to 90's

As stupid as this might sound, did any of you go into the sound control under XFCE and change the PCM **_and_** Master to 100%?

---

### Post by mark467 on 2008-10-10
I am not familiar with that. what and where is it?

---

### Post by dsbw on 2008-10-12
You can open up a terminal window and run

xfce4-mixer

which is very similar to the

alsamixer

progrm and the alsamixer GUI you can get to in the multimedia menu.

I'm having the same "low volume" issue. I've got to turn just about everything to 100%--TV, PCM, Master, Front, etc--MythTV's volume has no effect, I've just realized.

---

### Post by agamotto on 2008-10-12
> **mark467 said:**
> I am not familiar with that. what and where is it?

Go to the panel, and add volume control.  Right click on it, and there should be a preferences.  Choose Master, crank up to at least 90%, and choose PCM to do the same.  That seems to take care of it for most people who have asked me about this.  It is a pretty common *buntu problem with ALSA and PulseAudio updates.

---

### Post by mark467 on 2008-10-13
Thanks I will try that and let you know.

---

### Post by johnnybirdman on 2008-11-04
Any resolution on this?  I have tried several different setting for the audio, jacked up everything in xfce and still have to turn up the tv and amp volume way to high (so high I hear buzzing).
J.

---

### Post by dsbw on 2008-11-09
> **johnnybirdman said:**
> Any resolution on this?  I have tried several different setting for the audio, jacked up everything in xfce and still have to turn up the tv and amp volume way to high (so high I hear buzzing).
J.

Sounds like you've got the cable in the wrong place. (At least, that's what it means when *I* just get a buzzing.)

---

