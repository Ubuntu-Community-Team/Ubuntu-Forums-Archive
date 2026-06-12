---
title: "Sound is choppy when scrolling"
date: 2011-02-28
forum: Multimedia Software
---

### Post by Daswebmastri on 2011-02-28
When I am scrolling using my touchpad on my Dell E1505 regardless of which program, my sound skips. Its like it becomes scratchy or similar. I had the same problem with 10.04 and fixed it by modifying some modset file. Said it had something to do with my ATI X1400 GFX card too. Any ideas?

Thanks
-Das

---

### Post by tommcd on 2011-03-01
First, make sure the media player is not the active window when scrolling with the touchpad. This is so the touchpad scrolling does not try to act on the media player in any way.
Second, try opening **alsamixer** in the terminal and mute (or turn way down) the output channel(s) for the laptop's microphone. (There may be more than one microphone output listed in alsamixer). Then hit the **Esc** key to exit alsamixer. You could be getting feedback from the microphone input on your laptop from scrolling on the touchpad.
Hope this helps.

---

