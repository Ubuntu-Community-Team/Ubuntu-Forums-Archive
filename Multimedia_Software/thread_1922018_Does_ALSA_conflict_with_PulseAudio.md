---
title: "Does ALSA conflict with PulseAudio?"
date: 2012-02-07
forum: Multimedia Software
---

### Post by SnickerSnack on 2012-02-07
I've been having some sound problems, and I wonder if they might be caused by having both alsa and pulseaudio installed/running.

Problem 1: games run through wine lose sound randomly (maybe this is just wine, or a result of running steam, though).
Problem 2: Pressing the mute button on my new keyboard mutes both the alsa and pulse mixers, but pressing a second time unmutes only the alsa mixer, leaving no sound coming through the speakers.  I made a post about that here: [http://ubuntuforums.org/showthread.php?t=1821675](http://ubuntuforums.org/showthread.php?t=1821675), and since I suspect it may be a bug, I made a post here: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/912818](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/912818) (I'm zachery sharon in that thread).

I don't remember specifically adding packages to have both alsa and pulseaudio, but I did get diablo 2 running through wine a few years ago, so it's possible I added one or the other.

So, my questions: Should having both pose a problem?  Is it fairly straight-forward to remove one?

I'd most likely remove pulseaudio since Fallout 3 seems to need alsa for sound, though, as I said, sound dies randomly.

Edit: I've attached a picture of the alsa mixer.  How do I try switching which driver handles each item on that list?

---

### Post by Rodney9 on 2012-02-07
I don't run any Windows games, but I have Alsa and Pulse, no problem, can play music, videos, skype etc.

Rodney

---

### Post by SnickerSnack on 2012-02-08
> **Rodney9 said:**
> I don't run any Windows games, but I have Alsa and Pulse, no problem, can play music, videos, skype etc.

Rodney

Thanks for the reply.

Does your keyboard have a mute button?  Is it fully functional?

Do you have the alsa mixer gui?  If so, play some music, mute the master channel on the alsa driver, and then unmute the same.  Does sound come back on?

---

### Post by SnickerSnack on 2012-02-09
Problem #2 is solved by post #3 in this bug report thread: [https://bugs.launchpad.net/xfce4-volumed/+bug/883485/](https://bugs.launchpad.net/xfce4-volumed/+bug/883485/).

The solution in post #2 also reportedly works.

Problem #1 still stands, though.

---

### Post by MoreOrLess on 2012-02-10
> Does ALSA conflict with PulseAudio?
No. They're complementary.

Newer versions of wine play nicer with pulseaudio. See if you can find a ppa for wine1.4 in 11.10

---

### Post by SnickerSnack on 2012-02-11
> **MoreOrLess said:**
> No. They're complementary.

Newer versions of wine play nicer with pulseaudio. See if you can find a ppa for wine1.4 in 11.10

Actually, I have wine using ALSA right now since winehq says fallout 3 needs that setting.  I'll try them with wine using pulseaudio.

I'll try using wine1.4, thanks.

---

