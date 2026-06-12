---
title: "Resolution and refresh"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by NoWhereMan on 2006-02-11
I've just changed my old crt monitor with a new one (always crt, flatron, not sony), now the problem is that I'm *sure* I can take it to 1024x768 @100Hz, but on Linux this doesn't work: in the resolution panel of Gnome I can see only video modes that worked with the old (e.g. 1024x768 @85Hz). While it's years I'm accustomed to 85Hz my eyes would be glad of using another resolution.
Of course I dpkg-reconfigure xserver-xorg ;)
I tried adding a modeline 1024x768@100Hz, but X didn't like it (failed to start).
Using "ati" driver with a Radeon 7500.

Thank you :)

---

### Post by heimo on 2006-02-11
Check the /var/log/Xorg.0.log for warnings and errors.

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by NoWhereMan on 2006-02-11
my bad! :) I was putting the modeline in the wrong section!

---

