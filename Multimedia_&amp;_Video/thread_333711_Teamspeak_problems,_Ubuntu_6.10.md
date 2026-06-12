---
title: "Teamspeak problems, Ubuntu 6.10"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by StarsAndBars14 on 2007-01-07
Hey, I've got a problem on Edgy where if I join a teamspeak server I can hear other people but they can't hear me, even though the green dot lights up next to my name.  Sometimes people will hear echos of themselves if they try and talk to me.

I'm running ARTS with KDE and I've done it all according to this manual:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

using artsdsp.

My TS sound settings are driver /dev/dsp (I would use adsp but it mutes for some reason when I try to) primary sound device for capture/playback.

```

artsdsp -m /home/rgandy/TeamSpeak2RC2/TeamSpeak $*

```

A quick 'cat /proc/asound/cards' gives:

```

0 [V8233A]: VIA8233A - VIA 8233A
VIA 8233A with ALC 200,200p at 0xe400, irq 209

1 [UART]: MPU-401 UART - MPU-401 UART
MPU-401 UART at 0x330, irq 10

```

ls /proc/asound/card0 gives:

```

codec97#0 id oss_mixer pcm0c pcm0p pcm1p via82xx

```

and for /proc/asound/card1:

```

id midi0 oss_mixer

```

How can I fix this?

---

### Post by kebes on 2007-01-07
Alot of the time when I've seen this problem it's just as simple as the mixer settings being set wrong. Sometimes the teamspeak client uses a non-intuitive channel for its input, so go through all your mixer settings and try setting them higher/lower or on/off.

I've also found that teamspeak sometimes doesn't play well with other sound apps. Sometimes just having a music playing app open (not even running!) will mean that teamspeak doesn't work. I would try shutting down all audio devices (and games!) and seeing if you can get it working.

Also, never discount stupid things like your mic simply being busted (one time I had my mic plugged into the wrong port... duh!).

---

### Post by StarsAndBars14 on 2007-01-10
Tried both.  No worky.

---

### Post by StarsAndBars14 on 2007-01-13
Okay it seems to work to where I can hear a voice recording of myself now, I just went through this and applied parts 13 and 14.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

---

