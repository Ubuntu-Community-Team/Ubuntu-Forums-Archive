---
title: "Audio fails"
date: 2008-12-29
forum: Multimedia Software
---

### Post by rdionicio on 2008-12-29
This is a fresh install of Ubuntu and for some reason my audio just fails. It's on ALSA right now but when I click on "test" in the sound preferences I get

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
```

Any ideas as to why this happens?

---

### Post by frankelr on 2008-12-29
I had this problem when I enabled both my on board audio and my external usb audio.  Believe it has something to do with which audio card is being addressed first.  If you have two audio systems, try disabling one in your bios, than try the resulting sound playing option again.


Bob

---

### Post by rdionicio on 2008-12-29
Makes sense that it would work if I were to disable one or the other but what if I want to use both?

---

