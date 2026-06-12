---
title: "Upgraded to Gutsy 7.10 and now no sound"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by ZootNerper on 2007-10-26
Hi,

I just did an upgrade from Feisty to Gutsy and now the speaker icon shows sound muted. Single clicking does not get me the volume slider. Double clicking gets me a pop up window that reports:

"No volume control GStreamer plugins and/or devices found."

I have the GStreamer from my Feisty days.

If I go into System->Preferences->Sound all options except sound capture are set at auto detect. Clicking on test gets the following error in a pop up:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing

My user has "use audio" privileges.

No problems in Feisty. Two other upgraded machines (different hardware) don't show the icon/sound  problem. I don't have a sound card, using the built in sound on an ASUS P5LD2 SE motherboard.

Any ideas?

-- Zoot

---

### Post by ZootNerper on 2007-10-28
OK did a fresh install (actually to the AMD64 version of Gutsy) and now have sound.

---

