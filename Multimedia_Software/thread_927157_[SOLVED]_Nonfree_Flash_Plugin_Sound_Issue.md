---
title: "[SOLVED] Nonfree Flash Plugin Sound Issue"
date: 2008-09-22
forum: Multimedia Software
---

### Post by rivera151 on 2008-09-22
I don't know if this is an old issue or a new one, but I've searched the forums and the web about this and have not found a suitable fix or explanation.

The non-free flash plugin works, I can watch youtube videos quite allright, as well as other stuff.  The problem is that it hogs the sound output.  If I'm watching a youtube video (or anything that plays sound through flash) no other application will play sound (say, Rhythmbox, an embedded audio link within the browser, etc.).  It doesn't matter if I close or browse away from the site, I will not get my sound back.  I have to close Firefox to get it back and be able to play sounds.  

Is there a fix/workaround to this?  I think I read somewhere that it has to do with Flash using /dev/dsp directly, which locks it from other apps accessing it, but even if that was the issue I can't think of what I could do to subvert it.  I tried changing the /etc/firefox/firefoxrc line from "FIREFOX_DSP=none" to "FIREFOX_DSP=aoss" but that didn't do anything, so that leads to this post.

Thanks in advance.

---

### Post by Brain-free on 2008-09-22
Many. However many of them may not work for you.

I can tell you the most popular:

1)install the package libflashsupport from synaptic

2)Change your sound output to alsa (Right click on your volume icon, Preferences and choose the option with alsa)

---

### Post by markbuntu on 2008-09-22
You can try my guide, just scroll down to the Multiple Application Sound Sharing Section:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by rivera151 on 2008-09-22
> **Brain-free said:**
> Many. However many of them may not work for you.

I can tell you the most popular:

1)install the package libflashsupport from synaptic

2)Change your sound output to alsa (Right click on your volume icon, Preferences and choose the option with alsa)

Worked like a charm.  Thanks dude.  And thanks to markbuntu also.

---

