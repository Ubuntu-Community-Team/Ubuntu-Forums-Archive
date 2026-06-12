---
title: "Sound works for a bit... then doesn't"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by Sarisar on 2006-06-21
So turn on laptop, everything works fine, sound is great.

After several hours though, sometimes the sound stops.  I get errors complaining can't open sound, do you have a sound card and is it set up properly.

It's a compaq presario r3000 laptop with (according to linux) a geforce3 sound card on it.  Unfortunately I'm still a linux noob so some basic hints on what to look for may help (like which directories I need to look at!)

Thanks

---

### Post by Sarisar on 2006-06-25
Happened again (twice) today.

First time had Amarok open, had stopped for food, came back hit play and it skipped through every single song not playing them (had to kill Amarok in the end).  Tried a few other things and sound wasn't working but then hovering over an MP3 to get it playing seemed to unblock it.

Second time similar thing happened except I can't get the sound back again.

Anyone else having similar problems?

---

### Post by Sarisar on 2006-06-25
OK found more stuff out.  After sound died earlier, I was trying out some aggregators and when running akregator go a KNotify error.

```
During the previous startup, KNotify crashed while instantiating KNotify. Do you want to try again or disable aRts sound output?
If you choose to disable aRts output now, you can re-enable it later or select an alternate sound player in the System Notifications control panel.

```

What is that?  was that basically telling me my sound was dead and it restarted it.  Also can I manually do that to fix it if my sound goes again?

And what is the system notifications control panel?

---

### Post by LordRaiden on 2006-06-26
Can you look at the amarok configuration tab (offhand Tools >>> Configuration).

Look under engines. It might be set to arts or something. Trying setting it to alsa or oss (alsa is preferable).

---

### Post by Sarisar on 2006-06-27
OK changed it from 'autodetect' to alsa as recommended (thanks).  Will let you know what happens :)

---

