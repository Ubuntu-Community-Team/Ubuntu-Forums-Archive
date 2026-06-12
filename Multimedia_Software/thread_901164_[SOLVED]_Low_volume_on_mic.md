---
title: "[SOLVED] Low volume on mic"
date: 2008-08-26
forum: Multimedia Software
---

### Post by Fibonacci on 2008-08-26
Hey guys,

I recently discovered that my mic, which had worked fine under previous versions of Ubuntu, suddenly didn't work anymore. Fearing a hardware failure, I tested another microphone - one which I knew was working correctly (under Windows at least). And, as you might guess, it didn't work either.

So I ran gnome-volume-control, went to edit->preferences, checked every box, turned the Microphone volume all the way up on the Playback tab, did the same for the Capture volume on the Recording tab (the only volume bar in that tab), enabled +20dB Mic Boost on the Switches tab, and changed to from Mic1 to Mic2 on the Options tab.

Now, gnome-sound-properties seems to capture audio on the microphone and play it back very faintly - but still audibly; gnome-sound-recorder doesn't seem to record any audio unless I speak loudly right on top of the mic - so volume is still very low. arecord doesn't seem to record any audio unless I *tap* the microphone, and then, the recorded audio is very, very faint.

So. What's wrong with my system? What else can I try to get audio at a decent level from my microphone?

Thanks in advance.

---

### Post by Fibonacci on 2008-08-26
Update: it so happens that my mic works fine under Hardy LiveCD. By activating Mic Boost I am able to record and play back at a decent volume. Why, then, is this not the case on my installed system?

---

### Post by Fibonacci on 2008-08-26
It seems that the culprit was V_REFOUT. I checked it on Edit->Preferences, then set it to 2.25V under Options (3.7V works too, but the mic is not as sensitive). Now I can record sounds even without Mic Boost.

---

### Post by SanskritFritz on 2008-09-12
I have exactly the same problem in Kubuntu Hardy. Can you please tell me how to set this in KDE? I want to try your solution.
Thanks in advance!

---

