---
title: "i815 on-board vid issues"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by The Pinny Parlour on 2006-01-04
Having troubles with vertical lines spaced about an inch apart on a fresh installation of ubuntu.  Anyone got any ideas?  This is my first time, I'm an absolute newbie.  The newbie mods/people at the beginners told me to post else where regarding this issue.

TIA


Update:  Canned it and went with a different MOBO with AGP video card.  Working fine now.

---

### Post by Donshyoku on 2008-02-25
This thread is dated at the time of my post, but it came up with a system I recently bought used.  Ubuntu (up to Gutsy) gives it in "intel" driver in xorg, but you need to "sudo dpkg-reconfigure xserver-xorg" and follow the prompts.  When asked what video driver you want, choose the "i810".  I spent about an hour trying to figure this out today and this solved the issue.

So if Googlejuice brought any other posters here, that should fix the problem.  Long live old comptuers... :guitar:

---

