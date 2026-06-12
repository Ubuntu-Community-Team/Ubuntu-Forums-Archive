---
title: "Wireless mouse skips when sound is playing"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by pennstatebadboy on 2008-01-27
I did a fresh install of Gutsy on my machine. Things are working normally except that my wireless (USB) mouse doesn't work properly when sound is playing.

It skips and jitters. As soon as the sound stops, it's fine.

Is this an IRQ conflict? How do i fix this?

---

### Post by sleepingdragon on 2008-01-27
Just a quick question... Is your wireless mouse receiver next to your speakers? If so, try moving it and see what happens then.

---

### Post by pennstatebadboy on 2008-01-27
No. It's not near the speakers. Everything worked before as it is positioned now. The problem happened when I did a fresh install of Gutsy.

---

### Post by pennstatebadboy on 2008-01-27
bump

---

### Post by ubuntu-freak on 2008-01-27
> **pennstatebadboy said:**
> bump

 
You could always try
 
**sudo dpkg-reconfigure -phigh xserver-xorg**
 
Might set things up better or fix a slight bug.
 
Nathan

---

