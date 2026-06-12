---
title: "trouble playing videos in firefox... jaunty 64bit"
date: 2009-08-31
forum: Multimedia Software
---

### Post by Darkoblivion2 on 2009-08-31
hi all! hope someone can help me...

i have searched and googled, and i think i have messed things up now...

recently after a system update, i can no longer play quicktime trailers in firefox.
after looking for a solution, i have done alot of sudo apt-get's and removes, and i think that now i have too many plugins/codecs/etc and thats whats messing things up...

anyone know how to start from scratch, and make my computer do what i want it to?!

thanx in advance!

---

### Post by tgeer43 on 2009-08-31
Here's one possible idea:

Have a look in /var/cache/apt/packages. Normally a copy of every package you have installed is kept here. Get the package names of the plugins/codecs that you installed and apt-get remove them. Then run:
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```You might want to also install deborphan and run it to remove any orphaned files.

This should get you somewhere close to where you were originally.

Good luck,

tgeer

---

