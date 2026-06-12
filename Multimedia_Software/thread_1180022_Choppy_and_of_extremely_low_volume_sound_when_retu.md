---
title: "Choppy and of extremely low volume sound when returning from Suspend mode"
date: 2009-06-06
forum: Multimedia Software
---

### Post by yonyz on 2009-06-06
When Ubuntu returns from Suspend mode, the only sound I get when playing music is an extremely low (volume wise), choppy sound. I can't even tell if that choppy sound has anything to do with the actual music that is being played.
Also, when not returning from Suspend mode, I only hear sound from the right speaker. That is *not* the case with Windows XP.

My audio card is ESI Juli@, and I'm using Alsa ['ESI Juli@ (Alsa mixer)'].
The music is played through VLC.

---

### Post by Admiral Nesquick on 2009-06-06
Firstly, if only your right speaker seems to be giving sound, i would first check the volume mixer settings.

Secondly, what version of Ubuntu are you using ? If you use suspend mode a lot you should consider an upgrade to Jaunty. Other from that, what media player do you use in Windows ? In Ubuntu, check if the problem also occurs with Totem or Amarok. If it doesn't work in one of those two ( or others you might also try ) we'll see what we can do further on ;)

---

### Post by monraaf on 2009-06-06
I had a similar problem, the only solution that actually works for me is to reload alsa after a resume.

```

alsa force-reload

```

I have it in a script in /etc/pm.sleep.d/ so I don't have to do it manually after each resume.

---

### Post by yonyz on 2009-06-07
I've followed a guide to update mplayer, and it fixed the right-speaker problem.
I use Ubuntu 9.04 (Jaunty).

monraaf: It seems like an easy solution.
Can you please guide me, step by step, how to do it?

---

