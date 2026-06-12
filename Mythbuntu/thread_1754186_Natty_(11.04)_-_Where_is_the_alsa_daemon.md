---
title: "Natty (11.04) - Where is the alsa daemon?"
date: 2011-05-09
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2011-05-09
I just did a clean install of mythbuntu on a GT240 based system.  No audio.  The first thing I noticed is I don't know what the audio daemon is.  No more "sudo service alsa-utils restart".  Now it gives a "unrecognized service".

A check of /etc/init.d shows no real audio looking services.

Where did they go?

I guess I missed this train...

---

### Post by phroman on 2011-05-09
Are you looking for alsamixer?  At the command line type:

```
alsamixer
```

to get to your audio settings.  I've had a few audio issues myself lately and found the following article.  It's a year old, but I think still relevant.  

[http://www.tuxradar.com/content/how-it-works-linux-audio-explained](http://www.tuxradar.com/content/how-it-works-linux-audio-explained)

---

### Post by Dewey_Oxberger on 2011-05-09
No I'm looking for the sound service.  Back in 9.04 it was alsa-utils.  So when you made a change to asound.conf you would "sudo /etc/init.d/alsa-utils restart" (or in 9.10 you could "sudo service alsa-utils restart".

I assume audio still needs a service running.  Is mine missing or did it change names...  that's the question.

---

### Post by Dewey_Oxberger on 2011-05-09
Things keep changing I guess.  I'd love to learn the err of my ways here so if you can shed some light on this I'd be thankful:

1) I don't see the usual IEC958 devices in alsamixer.  If I enable everything in alsamixer I get no audio.

2) I have no idea where the alsa service is but I put a asound.conf that defaults a plughw:1,7 and did an old fashioned reboot.  I got no audio.
3) I ran the gui Mixer application (Applications/Multimedia/Mixer) and found the IEC958 devices in there.  I enabled them.  Now I have audio.

Wow. This seems strange.

---

### Post by psylencer on 2011-07-22
> **Dewey_Oxberger said:**
>  No more "sudo service alsa-utils restart". 
For anyone following deweys.asound.conf instructions where it refers to alsa-utils. Forget about it.  Mythtv .24 has software volume control built in.  Just select the "software" under the mixer device section and ensure your audio output device is set correctly.  (As in ignore deweys.asound.conf completely).  It is obsolete for those using mythtv > 0.24

---

