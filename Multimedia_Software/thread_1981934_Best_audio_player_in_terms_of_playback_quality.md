---
title: "Best audio player in terms of playback quality?"
date: 2012-05-17
forum: Multimedia Software
---

### Post by Yasashii on 2012-05-17
I'm a novice Linux user. Currently I'm using Xubuntu 12.04.

Since I don't have much experience with Linux multimedia software, I would like to get some opinions on which audio player is the best one **in terms of quality.**

The things I'm looking for in a multimedia player are: playback quality, ease of use, lightness. In that precise order.

There are plenty of "top ten Linux audio players" lists out there but they usually list the players considered best because of their look and overall ease of use. They don't usually mention playback quality which is the most important thing for me.

So what would you put on a list like that if playback quality was the main thing you base your judgement upon?

---

### Post by shantiq on 2012-05-17
i would say  **[XMMS]("http://ubuntuforums.org/showthread.php?t=1525072")** for me **without the shadow of a doubt**


a bit tricky to install but worth it   [i have tried them all and clear as a bell is Xmms]


if you want an easier install   **vlc  **also for sound [  **nvlc **from command line]


also **smplayer** has a great sound but more of a video player than audio


**=======================**



for sound  not quite in the same league insofar as my bat ears pick up::]]



  [**deadbeef**]("http://sourceforge.net/projects/deadbeef/files/debian/0.5.4/deadbeef_0.5.4-1_amd64.deb/download")       the link is for the deb   really easy to install therefore


also **aqualung**    but not as good for sound      > sudo apt-get install aqualung[B]
audacious[/B]  if you use the crystalizer plugin in effect plugin    but i still do not think the sound is as clear either

---

### Post by Vereinfachen on 2012-05-17
Yasashii,

In a computer you play back digital files, so it doesn't matter which player you use. They will most likely use the same sound backend anyway (gstreamer).

My favorite player is Quod Libet. It is used by many audio enthusiasts because of its awesome tagging capabilities. It uses (like pretty much any other player out there) gstreamer ;)

Just choose one that you like. :)

---

### Post by shantiq on 2012-05-17
> **Vereinfachen said:**
> Yasashii,

In a computer you play back digital files, so it doesn't matter which player you use. They will most likely use the same sound backend anyway (gstreamer).

My favorite player is Quod Libet. It is used by many audio enthusiasts because of its awesome tagging capabilities. It uses (like pretty much any other player out there) gstreamer ;)

Just choose one that you like. :)


with all due respect
test them all you will that is simply not the reality:KS

---

### Post by enigma32 on 2012-05-17
Many of them do use gstreamer, and they will sound the same.
You can sometimes change the library that is used for decoding files (such as the various different mp3 libraries that are out there), and that can make a difference.

If you're playing back raw wav files it shouldn't make a difference what you use, unless something is configured improperly.

---

### Post by Yellow Pasque on 2012-05-17
I personally use Audacious with a minor amount of Crystalizer plugin (and bauer stereophonic plugin when using headphones). This is on a system with Debian and no pulseaudio.

deadbeef uses a lot of the same libraries as Audacious and sounds similar to me.

A lot of players are probably going to sound the same if you're not using some kind of DSP plugin or equalizer.

Amarok (via Phonon), Banshee, Rhythmbox, Clementine, Totem, Parole, Songbird, yauap, quod libet and Guayadeque all use gstreamer. Theoretically, they should sound the same. I like the gstreamer delta plugin for improvement: [https://decatf.wordpress.com/](https://decatf.wordpress.com/) (as well as gstreamer bauer plugin for headphones).

@shantiq: Is xmms using any kind of DSP, or is it just playing directly through ALSA?

---

### Post by shantiq on 2012-05-18
it uses alsa


all the library players in my experience never have a really high sound quality [their primary aim is cataloguing/searching etc];    i hear always a minor muffle;  clementine the best of the lot but after a while i always head back to the topdogs

i have had this debate before about lossless formats too:KS:KS    there are elements which separate them all;    you could do an audio blindtest on lossless formats and players and i am sure i would find my way round

if anyone wants to hear it :KSagain [probably not:KS]  it goes shorten/alac/wavpack/tak/ofr/flac      then there are the one which are less clear like ape/tta     they all have different sound qualities none of these have been written in the same way and it in some ways impacts......

so for me sonic ecstasy   is **shorten on xmms **    sonic perfection

or of course 24-bit flac or wavpack on same

i am very short sighted but have the ears of a bat    [musician and linguist]

hey disregard all of this or better even    check shorten on xmms and tell me if you hear clarity.....:KS   [it was designed at cambridge university for speech]

---

