---
title: "Shockwave flash makes viewing of videos on firefox slow"
date: 2008-10-12
forum: Multimedia Software
---

### Post by micdhack on 2008-10-12
This is a really weird bug. I upgrade my ubuntu version to 8.10. Since then i am experiencing problem with my ALSA sound. If i go to setup my sound card to play with alsa i get this error on the test "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink". So i changed this to OSS.
In addition to this problem came the sudden loss of shockwave flash plugin on mozilla which enabled me to view youtube videos. So reinstall a new one and now i can see videos but some weird things are happening.

1)The firefox is eating alive my CPU. I mean is impossible to even have tab browsing when the youtube video is playing
2)Because of this CPU loading if the youtube videos has spikes and frame is not even 10frames/sec
3)After a while the sound get lost(this is probably because of the cpu loading im guessing or the is because of OSS)

As you can understand this makes totally useless the flash plugin on mozilla..any ideas?

UPDATE: I installed flash on opera browser and it works fine. So i think that this is a mozilla problem.
Also i ended up on having now 2 shockwave flash plugins on mozilla with no clue how to remove them. the first is 9.0 r100 and the second 9.0 r124 (which doesnt work).
UPDATE2: So i did a little more experimentation and i found out that if i delete the file that was in here
/usr/lib/swfdec-mozilla libswfdecmozilla.so the old buggy version dissapeared from firefox so now i have only the 9.0 r124. It works like charm except the thing that i dont have a sound.

---

### Post by eye208 on 2008-10-12
> **micdhack said:**
> This is a really weird bug. I upgrade my ubuntu version to 8.10. Since then i am experiencing problem with my ALSA sound.
Welcome to the world of PulseAudio.

If you want your previous ALSA setup back, see here:

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by micdhack on 2008-10-12
You mean that the new version now has PulseAudio as default? If yes how can i make it work?(little noobie question :D )

---

### Post by gandaran on 2008-10-12
before you do any pulseaudio fixes you should try this first, for flash 9 sound problems install libflashsupport or install flash 10 which fixes the sound issue. only then if non of these two options work you go for pulseaudio or alsa fixes
to remove flash use synaptic package manager, look for swfdec flash and the adobe flash 9 (flashplugin-nonfree) check also you don't have gnash flash intalled, mark for complete removal and click the apply button
get the flash 10 here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by micdhack on 2008-10-12
yeap that solved. there was no need for installing flash 10. only removing the rest of the packages and keeping the one libflash it was enough.
Still this doesnt solve my other bigger problem with alsa and the error iam getting upon testin "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink"
But flash and firefox work perfect now :)

---

### Post by eye208 on 2008-10-12
libflashsupport is not a solution because it makes Flash 9 unstable and crash-prone. You are going to find that out soon.

---

### Post by micdhack on 2008-10-13
you know when a guy heres unstable and crash-prone he certainly starts worrying :D

Well i installed pulseaudio device chooser and manager and i put every device on my sound to pulseaudio server. I find pulseaudio much more better because you can define which program uses which sound device which is great.
Since i fixed this i can now use other flash packages that support pulseaudio.
I think i also found a guide somewhere for connecting this two.

---

### Post by eye208 on 2008-10-13
> **micdhack said:**
> you know when a guy heres unstable and crash-prone he certainly starts worrying :D
I didn't mean to make him worry. I just wanted to point out that libflashsupport may prevent him from visiting some websites. Firefox will just close, that's all.

People usually blame Firefox or Flash for this, but that's wrong. Flash 9 with ALSA is 100% stable.

---

