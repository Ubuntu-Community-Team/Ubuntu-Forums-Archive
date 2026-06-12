---
title: "Weird VLC problem"
date: 2011-02-09
forum: Multimedia Software
---

### Post by holydogtoffee on 2011-02-09
Hi,

I have M-Audio 7.1 soundcard with profile "Analog surround 4.0 Output + Analog Stereo Input" in use from the sound preferences. (Using 2 speakers and headphones). Using newest Ubuntu and latest updates from repositories.

When I try to play a video the sound comes fine but after ~1min 27s (it's pretty much this every time) it stops. Debugger in console shows this:

[0x2587920] main audio output warning: output date isn't PTS date, requesting resampling (102552)
[0x2587920] main audio output warning: buffer is 96552 late, triggering upsampling
[0x2587920] main audio output warning: output date isn't PTS date, requesting resampling (54332)
[0x2587920] main audio output warning: audio drift is too big (161196), dropping buffer
[0x2587920] main audio output warning: output date isn't PTS date, requesting resampling (75662)
[0x2587920] main audio output warning: audio drift is too big (197379), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (167379), dropping buffer
[0x2587920] main audio output warning: computed PTS is out of range (708258), clearing out
[0x2587920] main audio output warning: timing screwed, stopping resampling
[0x2587920] main audio output warning: output PTS is out of range (714831), clearing out
[0x2587920] main audio output warning: output date isn't PTS date, requesting resampling (336192)
[0x2587920] main audio output warning: audio drift is too big (339234), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (288005), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (255817), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (238005), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (214109), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (163005), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (130692), dropping buffer
[0x2587920] main audio output warning: buffer is 113005 late, triggering upsampling
[0x2587920] main audio output warning: output date isn't PTS date, requesting resampling (226720)
[0x2587920] main audio output warning: computed PTS is out of range (754330), clearing out
[0x2587920] main audio output warning: timing screwed, stopping resampling
[0x2587920] main audio output warning: output PTS is out of range (765499), clearing out
[0x2587920] main audio output warning: output date isn't PTS date, requesting resampling (512738)
[0x2587920] main audio output warning: the mixer got a packet in the past (501904)
[0x2587920] main audio output warning: the mixer got a packet in the past (469904)
[0x2587920] main audio output warning: audio drift is too big (493488), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (455926), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (451780), dropping buffer
[0x2587920] main audio output warning: audio drift is too big (400926), dropping buffer

I can disable the audio track and toggle it back and I can hear sound for another 1min 27s, but then it's this all over again.

I've tried using different output modules from VLC (default/PulseAudio/ALSA) and it does this with everything. 

If I use default output module from VLC and "Analog Surround 7.1 Output"-profile from sound preferences the sound is continuous. However, there's a big flaw with this. VLC interprets my system as 7.1 architecture, which it is not since I would like to have identical sound outputs from headphones and regular speakers. My system handles my speakers as front speakers and headphones as rear ones. (Also in ALSAmixer)

So the sounds I hear from surround sound movies are only soundtrack and such which are usually played from front/rear speakers. Movie clips without surround sounds work fine.

How to correct this or to set it so that I can use 7.1, but with front/side/back left having the same output and vice versa for front/side/back right. I would be fine using the 4.0 system too, but it has the problem that the sound stops playing after a while.

---

### Post by holydogtoffee on 2011-02-10
Bump

---

### Post by stevo1977 on 2011-10-18
I am having this same problem.  The sound just cuts out after about a minute and a half.  If I shut off the track and turn it back on it works for another minute and a half and then cuts out.  Ditto for using different output modules.  This seems to be a relatively new development.  The video files I have noticed this on are all .avi's, if that helps.  Thanks.

Cheers,
stevo

---

### Post by stevo1977 on 2011-10-18
Update: same problem (though after a different time duration) when playing DVDs in VLC.  I am using VLC 1.1.11.

Cheers,
stevo

---

### Post by stevo1977 on 2011-10-25
No one is having/has had this problem?  Nothing?  Can I provide any more helpful information?

---

### Post by stevo1977 on 2011-10-26
Reinstalling seems to have fixed the issue for now.  Still not sure what was wrong, though...

---

