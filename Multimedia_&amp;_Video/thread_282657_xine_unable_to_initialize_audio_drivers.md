---
title: "xine unable to initialize audio drivers"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by theslut on 2006-10-23
Dapper has just stopped running in ALSA mode on Amarok with a "xine was unable to initialize any audio drvers" problem. Only the OSS will run Amaraok now.

I've no idea what went wrong but it happend the other day.

I've installed Edgy on another partition completely independantly and this also has ALSA issues.

The card i have (terratec 24/96) was running just fine before.

---

### Post by NyquistLimit on 2006-10-23
Is that Terratec card based on the Envy24 chip? I have an M-Audio Audiophile 2496 and several users including me have also been having problems with the alsa drivers (ice1712) in edgy.

---

### Post by theslut on 2006-10-23
i think so. It's certainly from that breed of early 24 bit cards that came out 6 or so years ago.

i removed my .asoundrc file in my home directory and ALSA playback is working again but the sample rate is screwed and it's sounding lower in pitch then it should be.

It's not just Edgy though, its Dapper as well since the other day (used to work flawlessly ](*,) )

---

### Post by NyquistLimit on 2006-10-23
Wow, deleting the .asoundrc file solved my problems! Now alsa works perfectly like it used to in Dapper! Thanks for that nugget of info :)

After spending so much time trying all the advice in the [sound problem guide]("http://ubuntuforums.org/showthread.php?t=205449") I can't believe the solution was so simple ](*,)

---

### Post by theslut on 2006-10-26
yeah, at the alsa homepage it says you shouldnt need one except in circumstances to override certain options.

---

