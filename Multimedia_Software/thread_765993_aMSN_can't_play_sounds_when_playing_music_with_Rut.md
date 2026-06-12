---
title: "aMSN can't play sounds when playing music with Ruthmbox"
date: 2008-04-24
forum: Multimedia Software
---

### Post by andrebrait on 2008-04-24
aMSN never played sound from the beggining, but someone told me to go to **Preferences > Others** and change the **Sound Server** from **play $sound** to **aplay $sound**.

This worked for me. Changing to **Use the Snack library** also worked...

But it won't play any sound when other programs are playing sounds...

I tested with every program I have, even trying different sound outputs...
All of them played the sounds with Rythmbox playing...

So... what can I do? :confused:

In Gnome's sound panel, I can't test the sound with ALSA or OSS. It give me the following message 

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
```

---

### Post by GeoMX on 2008-04-28
Same problem here, I have no sound in aMSN when Rhytmbox is playing (I guess any other application).

I have a Dell XPS M1330, just updated to Hardy from Gutsy, I had no problems in previous version :(.

Anybody knows what the problem is?

---

