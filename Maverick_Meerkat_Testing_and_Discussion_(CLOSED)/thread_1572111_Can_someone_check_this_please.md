---
title: "Can someone check this please?"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by reiki on 2010-09-10
In 10.10, are you able to copy an audio CD using Brasero?

This functionality is broken (bugged, but no resolution) in Lucid (Gnome) and I want to see if it's fixed in Meerkat.

Thanks,

---

### Post by cariboo on 2010-09-10
The bug isn't fixed yet, but in the bug report, they are trying to get it fixed before final release. See bug #[lpbug]529696[/lpbug]

---

### Post by mc4man on 2010-09-10
> are you able to copy an audio CD using Brasero?

Seems to be working fine here, 2 separate machines, at least in a copy to .iso  (completed fine

---

### Post by cariboo on 2010-09-10
The copy to iso works fine, it's when you want to make a CD to CD copy that the program fails.

---

### Post by mc4man on 2010-09-10
> a CD to CD copy that the program fails.
Don't see any issue there either.

The default for that would be to create an iso anyway, then automatically start the burn. While it works it seems to slow down the read quite a bit. ( slower than choosing to output to iso in the first place

Switching the option to copy directly to cd on another drive works fine and is significantly faster. 
In any case see no problems here though I tend to use ImgBurn anyway.

---

### Post by cariboo on 2010-09-10
When I try to do a CD to CD copy I get an error message saying:

```
cdrdao version to old
```

Which is referenced in the bug I linked to above.

---

### Post by mc4man on 2010-09-10
this is the version here - 
cdrdao (1:1.2.3-0.1ubuntu1) maverick
(- Robert Ancell <robert.ancell@canonical.com>  Fri, 10 Sep 2010 11:49:24 +1000

Edit:
> cdrdao version to old
taking a quick look at most likely places in brasero source don't see that message anywhere, plus I don't believe you can query cdrdao for version anyway
cdrdao -version
ERROR: Illegal command: -version

---

### Post by andrew.46 on 2010-09-11
Hi cariboo,

> **cariboo907 said:**
> The bug isn't fixed yet, but in the bug report, they are trying to get it fixed before final release. See bug #[lpbug]529696[/lpbug]

I am quite flattered that an [old guide]("http://ubuntuforums.org/showthread.php?t=795181") of mine [has been mentioned]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696/comments/22") as a temporary solution while the bug is being ironed out :).

Andrew

---

### Post by kuvanito on 2010-09-11
to me brasero is good for nothing(any ver of ubuntu) get k3b and problem solved

---

