---
title: "Fix Rhythmbox Freeze Media Keys"
date: 2008-07-17
forum: Multimedia Software
---

### Post by xavierzenith on 2008-07-17
I don't know how many people still have this problem, but it plagued my Ubuntu Hardy for days.

Symptom: When Rhythmbox is the active window (have focus), and the user was to use the media keys on the keyboard, rhythmbox would freeze for about 20 seconds (or longer) and resume functions.  -- This happened most with volume keys.

This solves the freezing, but you lose the ability to control rhythmbox through the media keys (except volume).

Solution: I think this should work for the problem, but in the process of acquiring the solution, I'd a lot of changes, so this MIGHT not be THE solution.

Steps:
Alt-F2: Enter "gconf-editor"
Go to: /apps/rhythmbox/plugins/mmkeys
Uncheck "Active"
Then restart rhythmbox if needed.

Like I said, this way you'll loose control of RB through media keys.

So decide for yourself if you want that.

Someone needs to look into this...

---

