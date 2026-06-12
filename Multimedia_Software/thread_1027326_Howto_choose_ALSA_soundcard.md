---
title: "Howto choose ALSA soundcard"
date: 2009-01-01
forum: Multimedia Software
---

### Post by mikeym on 2009-01-01
Hi,

I've got a problem slecting my soundcard. I have 2 soundcards in the computer one is a Soundblaster Audigy SE which I stoped usung before my new install because it didn't alow me to use my microphone the other is my onboard sound which untill I reinstalled was working well. Now when I slect it in **System > Preferences > Sound NVidia CK804 with ALC850 NVidia CK804 (ALSA)** I get this error:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.
```

But if I play sound with the following:

```
alsaplayer -o alsa -d hw:0,0 Music/The\ Very\ Best\ of\ Otis\ Redding\ -\ 15\ -\ Otis\ Redding\ -\ \(Sittin\'\ on\)\ The\ Dock\ of\ the\ Bay.mp3
```

It plays.

So how do I choose to use hw:0,0 for my sound?

---

### Post by Metaljaz on 2009-01-02
Give this a try:

System>Preferences>Sound 

Then try choosing the device that you wish to use.

---

