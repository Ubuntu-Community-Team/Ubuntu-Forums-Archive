---
title: "Creative X-Fi audio at test and login but not in media"
date: 2009-07-26
forum: Multimedia Software
---

### Post by drymedar on 2009-07-26
Hello!

I installed Ubuntu 9.04 the other day and installed Creative's drivers for the X-Fi series. When I tested the audio with this device: "Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA)" I get the error:

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

But when I test with this device: ""Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS)" I get sound. I also got that "du dun dun" sound at the login screen after I rebooted my computer and I also got sound in Rhythmbox, even though it sounded horribly. But the sound doesn't work in Firefox, SMPlayer (even though I changed the sound settings to both ALSA and OSS) or when I tried to play a song in Foobar2000 through wine.

Does anyone have a clue what might be wrong? If you need anymore info then just say so.

---

### Post by Taus on 2009-07-26
sound not working in firefox? when playing flash movies?

---

### Post by drymedar on 2009-07-26
Yeah, all sound works with the integrated sound circuit though, so I don't think it's got anything to do specifically with flash.

---

### Post by Taus on 2009-07-26
I have the same audio card and had the same problem as you. But i'm using the SPDIF output of the xfi so it might not be the same solution. I edited the asoundrc file and made a sink for the spdif in there. I had the same problem with xine.

---

### Post by Taus on 2009-07-26
you might also wanna check out which device rythmbox uses.

i beleive it uses the gstreamer config, so u should be able to find it by typing:
```
gstreamer-properties
```

---

### Post by drymedar on 2009-07-26
> **Taus said:**
> I have the same audio card and had the same problem as you. But i'm using the SPDIF output of the xfi so it might not be the same solution. I edited the asoundrc file and made a sink for the spdif in there. I had the same problem with xine.

That sounds hard :P

> **Taus said:**
> you might also wanna check out which device rythmbox uses.

i beleive it uses the gstreamer config, so u should be able to find it by typing:
```
gstreamer-properties
```

Under plugin it says "adjusted/customized" (don't know the actual words it says as I'm using the swedish version, so these are just my own translations) and under device it says "none".

---

### Post by drymedar on 2009-07-26
Just got it to work in SMPlayer, I had chosen the wrong setting in SMPlayer after all, but the flash problem is still there, though.

Edit: Okay, so.. now the audio works in SMPlayer but not in Rhythmbox nor Listen Music Player.

Edit2: Alright, got the music players to work by going into gstreamer properties and changing the plugin to ALSA, thanks for that tip!

---

### Post by Taus on 2009-07-26
do u have anything in your .asoundrc file?

---

### Post by drymedar on 2009-07-26
I can't seem to find my .asoundrc file, if I even have one. Doesn't seem like it's in my home directory where I read it's usually installed.

---

### Post by Taus on 2009-07-26
try to create an .asoundrc file by typing this in a console:

```
gedit ~/.asoundrc
```

then paste this inside it:

```

pcm.!default {
   type plug
   slave.pcm "surround51"
   slave.channels 6
   route_policy duplicate
}

```

restart firefox and try a flash movie. not sure if it will work, but it's worth the try :)

---

### Post by drymedar on 2009-07-26
> **Taus said:**
> try to create an .asoundrc file by typing this in a console:

```
gedit ~/.asoundrc
```then paste this inside it:

```

pcm.!default {
   type plug
   slave.pcm "surround51"
   slave.channels 6
   route_policy duplicate
}

```restart firefox and try a flash movie. not sure if it will work, but it's worth the try :)


You sir, are awesome.

Thanks so much for the help! Everything I need to be working is now working!

Do I add a "[SOLVED]" tag now or something or just let the thread be?

---

### Post by Taus on 2009-07-26
no problem, i'm glad my endless hours of non working x-fi cards finally paid out :)

got no idea about the [SOLVED] thingey - thats something i'm still trying to figure out.

---

