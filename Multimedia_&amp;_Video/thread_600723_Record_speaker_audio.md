---
title: "Record speaker audio"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by Hmarroqu on 2007-11-02
Is there a way to record the audio playing on speakers?

---

### Post by bingoUV on 2007-11-02
> **Hmarroqu said:**
> Is there a way to record the audio playing on speakers?

I am assuming you want to record it using a computer running linux.
You have a mic? Keep it in front of your speakers, connect the mic to the mic jack of your computer (sound card) and record from microphone. This will introduce noise. For better quality recording, read on.

Where is the audio coming from? If it is coming from the same computer on which you want to record the sound, just install audacity, and it can record wonderfully well. 

If the sound is coming from somewhere else, disconnect the audio-in jack from the speaker, and connect it to the line-in jack on the computer (sound card). Connect the speakers to speaker jack of your computer (sound card). If you play the sound, most likely speakers will play it. Now use audacity to record the sound, just ask it to record from line-in.

---

### Post by Hmarroqu on 2007-11-02
yea i should have been more descriptive...i would like to record streaming audio, needs to be of the same quality so i guess i will try audacity, i tired the sound recorder that comes with ubuntu but i did not knw what option to use.

---

### Post by mocha on 2007-11-02
Are you using an Intel HDA controller for your sound card?  If so let me know if you can get it to record the analog mix.  I cannot get mine to work even with the latest Alsa.

---

### Post by IGetMad on 2007-11-10
Well,

> You have a mic? Keep it in front of your speakers, connect the
>  mic to the mic jack of your computer (sound card) and record from microphone.

What all of you should know, is that only few people have a sound device (and Linux drivers which are supporting this) which is offering recording from the holy "stereo mix" port, which means recording exactly what the speakers are producing.

But this is exactly what many people need, in order to record live streams from an application, or something like this. So it should be possible to do it in a software way with ALSA, without installing extra software.

The ALSA docs state every time that it is very flexible, but (after googleing for weeks) I never found a way to do this. All I could find are explanations for how to record from Microphone or such stuff (which is trivial with a clean SuSE installation).

So, if anyone here could tell me how to record simply what comes out of my speakers, (Maybe especially on Suse 10, but its the same on Ubuntu I think), my thanks and good thoughts will always be  with you! :-)

---

### Post by Hmarroqu on 2007-11-11
To record quality streaming audio, i use the "mix" option on the default sound recorder in ubuntu.

---

