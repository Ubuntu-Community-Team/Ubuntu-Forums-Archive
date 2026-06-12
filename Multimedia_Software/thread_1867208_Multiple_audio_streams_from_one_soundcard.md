---
title: "Multiple audio streams from one soundcard?"
date: 2011-10-22
forum: Multimedia Software
---

### Post by Motley Fool on 2011-10-22
On my Ubuntu 8.04 system, I have ALSA and a soundcard setup.  It's working fine, and I can use it for:
[LIST]
[*]WAV recording (arecord -D hw:0 -f S16_LE -c1 -r44100)\[*]Helix (RealAudio) encoding
[*]Icecast/darkice broadcasting
[/LIST]

What I'd really like to do, though, is 2 or 3 of those at the _same time_, taking input from the sound card's LINE IN jack and encoding/recording it in several ways.

Is there a way to do this?  I've looked briefly at PulseAudio, JACK, etc. but couldn't easily determine whether those were what I needed (or whether they'd even work in Ubuntu 8.04)  In particular, old tools like Helix seem to be looking only for physical soundcards, so I assume that if this is possible, it would involve creating virtual soundcards that can be read from?

Thanks to anyone who can point me in the right direction!

---

### Post by Black_Sector on 2011-10-23
That would be awesome if we could stream out of all outputs at the same time. That way we just plug in what we want to use, wherever we feel like plugging it in, and the sound just works. No headache.

8.04 is OLD. Its not supported anymore.....It was a good release. Less buggy than newer ones. Outdated though. The new kernel runs laps around the old ones.

---

### Post by Motley Fool on 2011-10-23
Black_Sector, I should have clarified it's 8.04 LTS, still suppported on the server till 2013.

Does no one have any suggestions of how to make this work? :(

---

