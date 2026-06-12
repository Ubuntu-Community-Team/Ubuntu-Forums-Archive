---
title: "Problem with sound, will only play one audio source at once"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by simonjcruse on 2008-02-25
hi all, trying to get my sound card to play more than one source is proving to be a nightmare.. Trying to use it with alsa and the card in question is supported by Alsa, my other machine has the same card in and works fine, i have even checked the cards to see if it was faulty.

When im playing muic and i try to test the audio in system>prefs>sound i get this error:

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink 
profile=music: Resource busy or not available.

The hardware in question is:

Creative Live 7.1 24bit.

Any ideas? driving me mad..................

---

