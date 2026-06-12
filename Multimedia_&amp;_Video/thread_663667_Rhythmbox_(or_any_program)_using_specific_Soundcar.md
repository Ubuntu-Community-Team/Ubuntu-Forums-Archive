---
title: "Rhythmbox (or any program) using specific Soundcard?"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by jak-_- on 2008-01-10
I have two soundcards, one hooked up to my speakers and the other hooked up to my headset. Now, I usually listen to music via the speakers, but like to keep everything else, like mumble, on my headset.

I got this working with a little script using asoundconf to change the card to my speaker output and then revert to my headset output, however, asoundconf only seems to take any effect when run as root, which also means I either have to run the script as root or use gksudo.


```
asoundconf set-default-card V8237
rhythmbox
asoundconf set-default-card Live
```


Is there a way to do this without using root?

---

### Post by edm1 on 2008-01-10
Cant you just go System>Preferences>Sound then change each to it's appropriate sound card. We all look forward to Pulse Audio in Hardy.

---

### Post by mihai.ile on 2008-01-10
also have the laptop's default soundcard and the audigy, and also wait for Pulse Audio, hope it will resolve much of the sound problems we have in Ubuntu.

---

### Post by rubicon on 2008-01-10
**jak-_- **:
You can use CLI to control your app via command-line switches (however, rhytmbox doesn't have such switch for output device, it is a pity).

For example, ```
mplayer dvd:// -ao alsa:device=spdif -ac hwac3
``` (taken from here: [http://ubuntuforums.org/showpost.php?p=4093025&postcount=21](http://ubuntuforums.org/showpost.php?p=4093025&postcount=21))
Note, that 'alsa:device=_spdif_' uses mnemonic name from file '.asoundrc'. For your card, it should be raw, i.e. 'alsa:device=_hw:0_' or 'alsa:device=_hw:1_' (try both and notice what'll happen).

You can find exact command-line syntax for each app in manpages!

[quote=mihai007]and also wait for Pulse Audio, hope it will resolve much of the sound problems we have in Ubuntu.[/quote]It will be in the next release, Hardy Heron. For now, there are a couple of problems (also compatibility ones), that are stopping PulseAudio from being 'the sound panacea' :) But I also hope it will help to solve a lot of problems.

---

