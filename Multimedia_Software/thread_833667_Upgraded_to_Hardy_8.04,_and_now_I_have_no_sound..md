---
title: "Upgraded to Hardy 8.04, and now I have no sound."
date: 2008-06-18
forum: Multimedia Software
---

### Post by Cultural Savage on 2008-06-18
Last night, I upgraded from gutsy to hardy, and my sound didn't come with me. I have PC beeps, but have no volume nor any way to turn my volume up. 

So, don't know what's up or hat to do. Any help would be mucho appreciated.

Thanks!

---

### Post by kansei on 2008-06-18
Do you get any errors if you run alsamixer from a terminal window?

if not, use the left and right arrow keys to get to Master and/or PCM and then press the.. M button? or maybe the space bar to unmute them if they're muted, then adjust the levels.

---

### Post by Cultural Savage on 2008-06-18
> **kansei said:**
> Do you get any errors if you run alsamixer from a terminal window?

if not, use the left and right arrow keys to get to Master and/or PCM and then press the.. M button? or maybe the space bar to unmute them if they're muted, then adjust the levels.

I can't even get to my mixer at all. That is what Im confused about. I had em, now I don't

---

### Post by Exsecrabilus on 2008-06-18
Did you try the sticky: [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)?

---

### Post by Cultural Savage on 2008-06-18
> **Exsecrabilus said:**
> Did you try the sticky: [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)?

I tried the sticky just now, and I'm still getting this message when I try to open my volume control:

No volume control GStreamer plugins and/or devices found

???

---

### Post by kansei on 2008-06-19
hmm what does this give you?:

```

cat /proc/asound/modules 

```

---

