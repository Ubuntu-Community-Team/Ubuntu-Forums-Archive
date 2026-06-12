---
title: "SIIG SoundWave 7.1 PCI. I read that it works nicely. But I get no output. Help!"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Roasted on 2008-07-29
So, I did some research... came across a SIIG SoundWave 7.1 PCI sound card... looked good, 24bit, 96khz, 7.1, decent price, blah blah blah...

I read on NewEgg reviews that somebody got it to work flawlessly under Linux. They didn't say what distro, but I figured I'd give it a shot.

Just got it. Disabled onboard audio. Popped the PCI card in. I hear the two drum beats at the beginning where it prompts me for password... anything after... nadda.

I went to 'alsamixer' and tried muting + unmuting every option in the list. I'm not sure what could be causing the problem. Volume + PCM is of decent levels.

I am using Hardy Heron 64 bit, Alsa, and Amarok.
My speaker set of choice is a stereo system wired up through auxillary. Worked flawlessly for years.

What can I do?

---

### Post by Roasted on 2008-07-29
under sys - pref - sounds, when I hit "test" I have sound. Yet, Amarok plays nothing. Good signs, right? Now I just need to figure out which setting is bad... Any ideas? I can't seem to narrow it down.

EDIT - Works. Amarok was set to autodetect. This sound card, for whatever reason, doesn't allow things to be set to "autodetect"... but once they are set to my designated sound driver, in this case, Alsa, they work. I figured this out after VLC (set to Alsa) worked, but Amarok did not.

In essence, this card works out of the box with Linux... just as long as everything is set to Alsa (no idea if it works with OSS).

EDIT AGAIN - CNET.com and YouTube.com yield no audio. :( Help!
Also, I don't have the login sounds... I hear the drums before I log in, but the extended musical drums later I don't hear.

---

### Post by EdiferiousRex on 2009-01-02
I'm experiencing this same issue. Ubuntu 8.04 with the SIIG soundwave USB card. I have blacklisted the internal card, set prefrences to ALSA, receive sound on everything but youtube. Any ideas? I'll post a solution if I find one in the meantime. Thanks.

---

### Post by Roasted on 2009-01-04
Wait, wait, you get sound on everything EXCEPT YouTube? Really?

Are you sure YouTube isn't muted in any way?

Try going to another site that uses flash player and see if you can get sound there.

---

### Post by EdiferiousRex on 2009-01-04
You're right. No sound in other flash sites. Youtube is the only one I'd tried so far. Did you ever find a fix?

---

