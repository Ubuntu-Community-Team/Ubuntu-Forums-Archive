---
title: "Replay Gain"
date: 2013-07-31
forum: Multimedia Software
---

### Post by bill4 on 2013-07-31
I found "QT Gain".    this seems to be the 1 program we have that can set the replay/gain tags

now the General Objective is to have everything on the play list play at about the same level.

now generally speaking, if you are recording something you want to record it to 0db -- full modulation.    to do this with Audacity I've had to use my MM1402 mix board as a pre-amp -- or use the SOUND app -- to set the record volume

on a RIP CD the digital recording is already made

now as I understand it the Replay Gain tag is supposed to direct each track to a defined standard -- they call it "89db" -- why the departure from "0 db" i have no clue.

anyway, QT Gain creates the tags -- after you figure out how to configure it -- and then you find out it goes off half cocked ( yuk ) but I'll write a review on this later.

also: it doesn't present its results for review; it just ducks back in its shell

you can however inspect the tags using VLC and when you do this you find them set or at least VLC display data that indicates they are present and set to 89:
e.g. :

[IMG]http://ubuntuone.com/5PlRjmPIt7FNq8TGOtDFMc[/IMG]

Now, the Critical Question:    how do we get players -- like VLC or Audacious -- which say they support Replay Gain -- to honor the specification ?

---

### Post by CatKiller on 2013-08-01
You never want to record at 0dB Full Scale. The lack of headroom is what made ReplayGain necessary in the first place.

The ReplayGain specified nominal level is 89dB SPL, per the SMPTE recommendations at the time. In practise it uses -14 dB FS.

QT Gain isn't the only tool for writing ReplayGain tags. Personally, I use mp3tag or metaflac to do it, since you can do batches easily that way. Never had a problem with either of these.

I don't use VLC or Audacious, but in Amarok it's just a Preferences setting for whether it uses the Track tag, Album tag, or ignores them completely. I'd be surprised if either of the other programs were vastly different in that respect.

---

