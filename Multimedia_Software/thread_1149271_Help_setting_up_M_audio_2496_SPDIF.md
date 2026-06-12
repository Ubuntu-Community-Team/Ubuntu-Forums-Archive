---
title: "Help setting up M audio 2496 SPDIF"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Tokyo_Joe on 2009-05-05
I've been trying to set up my M audio 2496 soundcard for a while in Jaunty and can't get it to work exactly right. It's fine in Windows, so there's no hardware problems. All I want to do is have music and DVD sounds output from the SPDIF to my Amp.

In Alsa the only thing which worked was AC3 passthrough. Beautiful Dolby Digital and DTS movies but music files produced only silence. A DTS Wav file sample I downloaded worked OK though as did, for some reason, other Wav files samples I downloaded. Which is strange as audio CDs were silent.

So, noting that OSS v4 supports my soundcard I switched over. I like the Ossxmixer, very informative. Now I get great music from some music players (not all for some reason), but no ac3 passthrough. Playing Dolby Digital or DTS movies produces only stereo PCM in my amp. Strangely enough the sample DTS Wav file I downloaded earlier works just fine. But only when played in Audacious, not in anything else.

Is there anyone out there who can guide me through this setup, in Alsa or OSS? I don't care which so long as it's all working at the same time!

---

### Post by sonicb00m on 2009-05-05
I can't be of any help as the darn thing doesn't work at all for me either. I'm just contributing here so it's easy for me to find the thread again :D

I think it's a problem trying to run it in digital mode.

---

### Post by Tokyo_Joe on 2009-05-05
Well, I switched back to Alsa (which works with AC3 output autmatically), installed the Envy 24 mixer thing, fiddled a couple of switched (SPDIF out to Digital mix L and R) and now I have music! Seems to be playing my 44.1 khz files at 48khz which is somewhat annoying but I'll probably figure that out soon.

---

### Post by Tokyo_Joe on 2009-05-05
Hmph. Haven't sorted out my problem completely yet. Now I have to manually switch the mixer from 'Digital' to SPDIF Output whenever I change from music to DVD, which is annoying. Some of my music players don't work any more and VLC seems to have died. Also don't seem to have 'bitperfect' sound any more, I guess that's a result of routing through the mixer. It's gonna take a while to figure all this out. Will stick with ALSA for now as my microphone doesn't seem to work in Ossv4. Anyone know if I'm wasting my time and it just 'doesn't work yet' in Jaunty?

Just this, the monitor resolution thing and my suddenly messed up keyboard to figure out and I'm done. At which point it'll be time to upgrade Ubuntu and bugger things up all over again. :P

---

### Post by Tokyo_Joe on 2009-05-06
Great, got it working now. Using Amarok 1.4 all I had to do was change the Stereo Alsa Device from 'default' to 'iec958' and now it works Bitperfectly, and automatically changes to AC3 when I want it to.

Oh wait, changing to the next track causes a Xine error and everything dies. Hmmm...

---

### Post by sonicb00m on 2009-05-09
yeah I have just resigned myself to knowing that the unit isn't going to work properly.

I have an onboard sound card with digital output and am using that in Linux. It's working near-perfectly now.

The 24/96 card i only use in windows for audio recording.

btw, do you know how i can enable the 24/96 mode for recording in windows? I cannot get it to go into 96khz mode if any inputs or outputs are selected!

---

### Post by Tokyo_Joe on 2009-05-12
OK, I set audio drivers to 'plug:iec985' in Xine and Amarok settings (Amarok 1.4 since 2.0 doesn't seem to come with a settings option!?) and everything seems to work OK. Should I change the Audacious setting too? That's just 'iec958'. Is it the same thing? What's a 'plug'? Hmmm.

Next step seems to be to make an "asound.conf" file someplace and change the default Alsa driver to iec958 which presumably will let all those audio players which can only use "Default" work. I suppose.

Well, it's nice to have Amarok working at 44.1khz and automatic AC3 passthrough. I imagine nobody bothered to help us out as people have been asking about variations of this problem all over the place and the answer is *kind of* out there if you have several days free to hunt it down over a load of different forums.

Ho hum, live and learn I guess. Next month I'll read through every single 'resolution problem Xorg editing' thread to try to track down my missing 1920x1080 resolution.

Any luck with your card so far sonicb00m?

---

### Post by Tokyo_Joe on 2009-05-14
Made a file ~/.asoundrc  

Looks like this:

pcm.!default iec958:M2496

Now all the other players (and Youtube!) work just fine. Strangely enough Amarok still has fatal Xine errors ('cannot initialise alsa driver' or something) if you point it at default.
Works fine routed directly to iec958 though. 

AC3 passthrough not broken yet!

Playing a 96khz sample Wav produces static for some reason, worked fine under oss v4 though. Anyone have any ideas how to actually utilise the 24/96 of my M2496?

---

