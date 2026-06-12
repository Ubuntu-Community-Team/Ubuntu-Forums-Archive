---
title: "fix for ff is you enable uncompatable addons"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-01-05
messing around and enabled all extensions that were not compatible with ff 
4 beta 8 (the default version in ubuntu 11.04) to work. dont do this it borks ff. i had to close ff and enter this in the terminal: firefox --safe-mode
this will disable all ext. restart ff and it should work. then log off and relog on. fixed it for me

---

### Post by jfernyhough on 2011-01-05
Actually, not all extensions create problems. You just have to be selective; I've been happily running nightly builds (Minefields) for years with no major issues.

I'm not sure why you had to log off. Simply starting in safe mode (with -safe-mode), disabling extensions, then closing and loading Firefox again should work fine.

If you are using pre-release versions of Firefox I'd also suggest you back up your Firefox profile, in /home/[user]/.mozilla/firefox/. Then if necessary you can simply delete the broken one and use the older working version.

On some occasions the file compatibility.ini can cause problems when upgrading Firefox versions. I regularly delete it from my profile directory. Finally, deleting cookies.sqlite can (inexplicably) fix some problems, for example some extensions not loading (e.g. Delicious).

---

