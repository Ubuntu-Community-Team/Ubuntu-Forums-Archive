---
title: "broke unity"
date: 2010-12-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hsartoris on 2010-12-17
i have had the 11.04 release for about 5 minutes, and i already broke it. i was trying to enable desktop cube in ccsm, and ended up disabling unity. now, there is nothing except for nautilus.

is there a way that i can reenable unity without messing up my classic desktop?

---

### Post by garvinrick4 on 2010-12-17
Go into classic and:
```
ccsm
```check unity plugin on very bottom.

#can logout from terminal with: (if needed) CTRL/ALT/T
```
gnome-session-save --kill
```

---

### Post by mc4man on 2010-12-17
Once you get your _Desktop Edition_ login squared away with unity working, if you wish to enable cube/rotate let me know - fairly straightforward, a few possible bumps.

If you haven't already updated compiz to todays ...0ubuntu4 version you may wish to hold off a bit, it could have some issues. (if you already have and it presents no problems for the Desktop login, well that's good.

Personally I'd re-enable the unity plugin in the Desktop login, though you can in the Classic (you can actually run unity from the Classic login though again I wouldn't.

I only use the cube for scroll on desktop, works quite well, screen shows the the middle click rotate  - though in this install I have enabled the 'true' autohide so no launcher is seen. (the intelli-hide mode has issues, I actually prefer a real autohide on a desktop anyway

---

