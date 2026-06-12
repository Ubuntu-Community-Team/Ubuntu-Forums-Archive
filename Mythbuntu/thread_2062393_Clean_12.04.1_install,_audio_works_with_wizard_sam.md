---
title: "Clean 12.04.1 install, audio works with wizard samples, static otherwise"
date: 2012-09-24
forum: Mythbuntu
---

### Post by nickswanjan on 2012-09-24
Hello, I just finished a clean install of Mythbuntu 12.04.1 and everything is working well except audio output.

I selected my HDMI audio output in the setup wizard, and it works fine in the setup wizard including playing both of the sample videos, but it plays digital static when I try to view live tv or recorded content. Any hints to debug? Is some setting getting applied in the wizard but not for normal playback?

---

### Post by nickrout on 2012-09-24
try setting it to only output 48kHz audio (it is in advanced audio setup in mythtv)

---

### Post by nickswanjan on 2012-09-27
Tried the 48khz setting, but it still does not work.

I get the correct white noise when I test in audio setup, but I get a machine gun type noise when I try to view live tv or a recording.

---

### Post by anonymousdog on 2012-09-29
That reminds me of the sound I got when setup for DTS passthrough when there was no DTS signal.

---

### Post by nickswanjan on 2012-09-29
> **anonymousdog said:**
> That reminds me of the sound I got when setup for DTS passthrough when there was no DTS signal.

Aha! Turning off DTS did not fix my problem, but the idea got me turning off other items, and turning off Dolby did fix it - thanks!

---

