---
title: "Error in Testing under Sound Panel"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by johntkucz on 2007-07-05
Wheneer I click on a test button for soundplayback (music and movies; sound events, sound playback) whenever  ALSA is selected under the sound control panel.  I get this error (by the way, sound has yet to still work on this mx3701 gateway laptop):

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

---

### Post by RobMBaker on 2007-07-07
Same here - only thing that works for me is USB Audio ... but that doesn't work for system sounds (log in and out sounds etc.)

---

