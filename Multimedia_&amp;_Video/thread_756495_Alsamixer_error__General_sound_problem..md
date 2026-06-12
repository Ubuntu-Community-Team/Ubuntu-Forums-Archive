---
title: "Alsamixer error / General sound problem."
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by v3trae on 2008-04-15
I've been in IRC all day and i think my problem might be too intense for people to be interested in helping (and i don't blame them D;) Anyway. I'm having some strange sound problems. Amarok will play music, but none of my other programs can. Firefox, vlc, pidgin, mplayer all wont touch my sound card. 

I have a feeling it is a general problem with alsa talking to my sound card, i have a SB Live! 24-bit external, and i've been having a hell of a time getting it to work at all.

The thing that baffles me the most is when i run alsamixer in a terminal, i get the following

v3trae@lolbuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
v3trae@lolbuntu:~$ 

That's something i've never seen before and really have no idea what it means.

Any help is appreciated, if you need any specific information just ask (and if you could, tell me how to do whatever your asking in-case i'm not familiar with it).

Thank you!

v3trae

---

### Post by BetterSense on 2008-04-16
I've had a similar problem with a USB soundcard recently. Only rhythmbox, amarok etc work. No youtube, mplayer, etc sound.

---

