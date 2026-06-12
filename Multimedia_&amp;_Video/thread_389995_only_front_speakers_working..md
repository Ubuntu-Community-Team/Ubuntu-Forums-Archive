---
title: "only front speakers working."
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by Naegling23 on 2007-03-21
I just upgraded my onboard sound to a creative audigy 2 se soundcard because my onboard could not decode audio from mythtv without squeeling like a pig, and compusa is closing stores.

The sound card works, but only for my front two speakers.  The rest are not working (I have a 7.1 system, set to standard 7.1, ie not upmixing).  Does anyone have any idea why the rest of the speakers are not working?  (The speakers work in my other kubuntu box, and I have tried setting amarok to output to 7.1, but they just dont work).

---

### Post by flossgeek on 2007-03-21
Have you tried typing into a terminal:-

```
alsamixer
```

Ensure all the appropriate channels are raised. Then you should here sound in all your speakers.

---

### Post by Naegling23 on 2007-03-24
yup, nothing is muted, except for my IEC958 switch, if I unmute that, then I recieve no sound whatsoever.  

So I narrowed it down a little bit, if Im running mythtv, or just the backend, then I get only 2.0 sound.  I can get 7.1 out of amarok, but only if I kill mythbackend....which makes me think its a myth problem.  If I select dsp in myth, I get 2.0 out of my front speakers, if I choose adsp (alsa mixer) then I get 2.0 sound out of my rear two speakers only.

I have tried to troubleshoot this problem for a week and a half, im about to just give up.  its driving me crazy that I cannot have surround sound on my HTPC!

---

### Post by flossgeek on 2007-03-25
It does sound like a myth TV issue, have you checked there forums.

---

### Post by Naegling23 on 2007-03-26
I think I solved my problems.  The mythmusic, mythtv, and default dvd player in mythdvd do not support surround sound.  I changed the dvd player to xine, and got 7.1 surround sound coming out of my speakers.  Now I was hoping that mythmusic would duplicate that sound accross my speakers much like amarok does.  It doesnt do anything function wise, but its just nice to have the extra volume.  Since mp3's and native television are 2.1 channel, thats all I get from those sources.  I will have to check and see if a dolby digital television signal will work on my system or not.  Its dissapointing, but as long as my dvd's are working, im at least satisfied.

---

