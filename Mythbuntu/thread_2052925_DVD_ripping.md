---
title: "DVD ripping"
date: 2012-09-04
forum: Mythbuntu
---

### Post by AlecJ on 2012-09-04
I love Handbrake but.. why can't it read encrypted DVD's yet?

I find I have to reboot into XP to use DVDfab to rip most of my DVD's, and quite often I have to update DVDfab too.

Possibly a rooky question :- but how can they continue changing the way the disc's read (damaged clusters and so on) and yet they still work in "normal" standalone DVD players ?

If it's just that the standalone has firmware that skips damaged bit's or whatever, why can't Handbrake?

---

### Post by klc5555 on 2012-09-04
You just need to keep a wide array of ripping tools, because no single one works on everything.

For example, Lionsgate (beginning evidently with Hunger Games) appears to have instituted a new copy protection scheme that incapacitates HandBrake (also CLI tools like vobcopy). During the initial analysis of the 14 titles on the disc, the program simply fails to make it through the analysis of title 11 or 12. The log fills up with dvdnav errors and HandBrake is done.

VLC has no trouble with it however. And as you are already aware, Windows tools like DVDFab have already been patched to overcome the issue. So all in all much less annoying than the Paramount thing from a year ago.

You have to wonder why the studios continue to waste so much energy on this silliness.

As to perceived feature limitations of HandBrake itself, you'll have to take the discussion to HandBrake's own forums at: [https://forum.handbrake.fr/](https://forum.handbrake.fr/)

---

