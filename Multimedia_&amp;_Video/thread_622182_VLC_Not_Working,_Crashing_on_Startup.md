---
title: "VLC Not Working, Crashing on Startup"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by RPG405 on 2007-11-24
Hi,
VLC is not working. Before the problem, it was working fine, and one day, it just decided to stop. Whenever I try to open it, the GUI flashes on screen for a fraction of a second, and promptly disappears. This happens EVERY time I open it, not just when I run it under certain conditions or try to play certain video files in it. I've attached the output I get when I open vlc from the command line (split into 2 files). It seems to core dump, but I can't put any of it together.

---

### Post by rsambuca on 2007-11-24
Have you tried re-installing?

---

### Post by RPG405 on 2007-11-24
Yes, I've tried reinstalling, and then doing a "complete removal" on VLC and all VLC related packages and installing them agian, to no avail.

---

### Post by thewump on 2007-12-29
Any resolution on this thread?  Looks like I'm having the same issue.

---

### Post by RPG405 on 2007-12-29
I reinstalled Ubuntu from CD. That fixed it.

---

### Post by mc4man on 2007-12-29
@thewump 
before reinstalling ubuntu you could try reinstalling -  libwxgtk2.6-0

you might also try opening vlc in terminal with
G_SLICE=always-malloc vlc

---

### Post by Craigus on 2007-12-29
Probable solution in this thread:

[http://ubuntuforums.org/showthread.php?t=613023]("http://ubuntuforums.org/showthread.php?t=613023")

---

