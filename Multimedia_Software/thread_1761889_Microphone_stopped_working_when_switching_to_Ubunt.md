---
title: "Microphone stopped working when switching to Ubuntu"
date: 2011-05-18
forum: Multimedia Software
---

### Post by SwingKid on 2011-05-18
As the thread title describe it. My microphone worked fine in Windows, but now when I changed to Ubuntu (10.10) it stopped working. When I click on the little sound effect icon and click unto "Input" it doesn't say anything in the "Choose a device for sound input" and the input volume bar is locked and almost not visible. 
What is wrong and how can I fix it?

It is an inbuilt microphone on a notebook.

Thanks heaps!

---

### Post by ajgreeny on 2011-05-18
Try this:-
ALSAMIXER
Run alsamixer in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

You may find that the mic is muted, as this appears to be the default setting as far as I can make out.  Go to that channel in alsamixer, hit M and then set the level as you need it.

---

### Post by SwingKid on 2011-05-18
How do I start Alsamixer in the terminal then?

---

### Post by ajgreeny on 2011-05-19
Open terminal from applications ->accessories -> terminal and type **alsamixer**.  You will see a screen within the terminal like my screenshot.

---

### Post by SwingKid on 2011-05-21
> **ajgreeny said:**
> Open terminal from applications ->accessories -> terminal and type **alsamixer**.  You will see a screen within the terminal like my screenshot.

Cool. Thanks now it is fixed! :) Cheers!
:guitar:

---

