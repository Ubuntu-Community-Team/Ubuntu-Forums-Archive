---
title: "How do I install a microphone?"
date: 2010-03-29
forum: Multimedia Software
---

### Post by justint on 2010-03-29
Hi

Any ideas how to install a microphone on the system?

I have a microphone but when I plug it in it is not seen by the system.

Thanks

Justin

---

### Post by ajgreeny on 2010-03-29
What do you mean by "it is not seen by the system"?  How do you expect it to be seen?

If it is a usb microphone it should show in ```
lsusb
```but if it is plugged into the soundcard socket it will not show anywhere, as far as I'm aware.  I suspect, however, that it may simply be that the mic is muted or its level set far too low.

Run ```
alsamixer
``` in terminal and use the cursor keys to move sideways and raise and lower the sliders, use "M" to mute/unmute and tab to move from *playback* to *capture* to *all* then use Esc to quit and save settings.  You may find your mic is set too low in that, and be able to raise its level.

---

### Post by uberlube on 2010-03-29
if its a usb mic u may have to create a new .asoundrc
a quick google will lead you to the documentation.

---

### Post by justint on 2010-03-29
> **ajgreeny said:**
> 
Run ```
alsamixer
``` in terminal and use the cursor keys to move sideways and raise and lower the sliders, use "M" to mute/unmute and tab to move from *playback* to *capture* to *all* then use Esc to quit and save settings.  You may find your mic is set too low in that, and be able to raise its level.


LOVELY!!!! Thanks. It is a normal plug in mic.

That works a treat :) :) :) Thanks

---

