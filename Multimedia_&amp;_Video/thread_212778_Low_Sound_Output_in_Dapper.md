---
title: "Low Sound Output in Dapper"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by CodeMonkeyX on 2006-07-10
Hi all,
I have been playing around with two different distros recently (Suse 10.1 and Kubuntu 6.06) and I have noticed a problem with Kubuntu on my system.

Note: I have a Creative Sound Blaster Audigy2 Game ZS.

The sound output is very low, and it seems like the sound is distorted (too much base and treble). I tried playing with the mixer both in KDE, and the alsamixer in the console with no luck.

I install Suse 10.1 and the sound is perfect, no distortion and the volume is at expected levels. But I was having font issues in Suse. ;)

Anyway, I was having other issues with Suse not being very cutting edge, and I want to use Kubuntu. But I have to get this sound problem fixed.

I was considering re-compiling ALSA, like the sticky post said, and see if that helps. But I can not do that until tomorrow. Any other suggestions for thing I could try would be great.

---

### Post by CodeMonkeyX on 2006-07-11
Played with the mixer some more and found the problem. I had to activate nearly every control in the mixer, and in the end had about 30 sliders on the screen. Then I played with each one until I found the one I needed.

It seems that on the Audigy 2 ZS the headphones go into the Front Speakers connection on the sound card. So I had three sliders that controled sound to the speakers and the headphones:

1. Master
2. PCM
3. Front

Also I think the bass distortion was called by the front speakers being so low. I had to turn the amp up high to hear anything, so the sub was getting a good signal, and the front and center speakers were getting a low signal. Sooo way too much base output.

The Ubuntu guys might want to look into the default mixer setting for this card. Because like I said Suse 10.1 sounds awsome out of the box, it would be nice if Ubuntu did too.

---

### Post by elispiro on 2006-07-11
Heh, I have a SoundBlaster Audigy 2, also, CodeMonkey! I use headphones, and my problem wansn't much of a problem, but there were some points that I would have liked my maximum volume to be a bit higher. I adjusted what you said worked, and voila! I had slightly louder sound!

Thank you very much, CodeMonkey! :-D

---

### Post by CodeMonkeyX on 2006-07-11
> **elispiro said:**
> Heh, I have a SoundBlaster Audigy 2, also, CodeMonkey! I use headphones, and my problem wansn't much of a problem, but there were some points that I would have liked my maximum volume to be a bit higher. I adjusted what you said worked, and voila! I had slightly louder sound!

Thank you very much, CodeMonkey! :-D

Yeah I did not have too much of a problem with my headphones, the main problem I was having was with my 5.1 Surround speakers. The Sub was really loud and the others were too quite.

Also I hate having to max out my Master and PCM levels to 100% it distorts a little. So this makes it a little nicer.

Anyway, I am really glad my post helped you out a little. ;)

---

