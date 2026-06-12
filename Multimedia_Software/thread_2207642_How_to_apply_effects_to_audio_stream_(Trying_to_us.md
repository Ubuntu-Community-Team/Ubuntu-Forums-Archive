---
title: "How to apply effects to audio stream? (Trying to use ubuntu as audio workstation.)"
date: 2014-02-24
forum: Multimedia Software
---

### Post by reuben3 on 2014-02-24
I have an M Audio Delta 44 which I just hooked up to my computer. I'm playing an audio stream into input 1, and I want to route the audio through effects (e.g. rakarrak) and then listen to it via my regular soundcard. I fiddled around with envy24control and alsamixer, and something(?) I did enabled the input - so I can now see that there is input on the vu meter. However I'm stumped on how to get the sound to come out of my regular sound card (or, for that matter, back out of the m-audio).

Ardour won't load (some jack issue). Rosegarden looks like it has potential, but isn't showing any audio as input in the audio mixer. Rakarrak looks pretty cool, but I can't figure out the UI.

Can somebody help me get off the ground?

---

### Post by reuben3 on 2014-02-24
It seems to me that Jack is basically incompatible with whatever Gnome uses by default (pulseaudio/alsa?).

As soon as I start an application that requires Jack, any sounds produced by regular apps (radiotray, chromium) are killed, and nothing I do seems to make them come back. Restarting the X server leaves with the M Audio as the only sound device in Sound Settings, and since I haven't figured out how to get sound OUT of the M Audio interface that sucks. The only thing I've found that works is a complete restart.

And wow are the UIs of the main audio apps (i.e. those recommended by ubuntu studio) harsh on the eyes. Too bad, I was hoping things had improved in this area since I'd last experimented with them (2006 or so). I'm sure there's some power here but it's hell in terms of usability.

---

### Post by tgalati4 on 2014-02-24
I have a Delta66 and it works pretty well under linux.  You have to set the patches correctly to route input to output to get a monitor of sound on Input1.  As far as Jack audio, it requires some configuration.  Are you using Ubuntu Studio?  You can change the themes and colors of apps if they are distracting.  

Linux still requires quite a bit of fiddling to get working correctly.  That has not changed since 2006.

You need to get into the details of [JACK]("https://help.ubuntu.com/community/What%20is%20JACK") to appreciate its quirckiness.  It is not plug-and-play.

---

