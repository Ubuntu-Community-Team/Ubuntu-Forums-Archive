---
title: "Mythbuntu records everything I watch, nothing I program"
date: 2009-01-19
forum: Mythbuntu
---

### Post by Crusty Juggler on 2009-01-19
I'm sure this is a simple configuration fix, but I'm not sure where to look.  Shows I program to record don't, but anything I watch ('Watch TV') shows up in Recordings.

What have I set up wrong?

---

### Post by utar on 2009-01-19
> **Crusty Juggler said:**
> I'm sure this is a simple configuration fix, but I'm not sure where to look.  Shows I program to record don't, but anything I watch ('Watch TV') shows up in Recordings.

What have I set up wrong?

I would guess you have the "live-tv" filter selected in show recordings rather then "default" which will show you the recordings.

I forget the key to change filters as these are all mapped on my remote, try pressing the the right arrow key a few times or m.

You can also check /var/lib/mythtv/recordings to see if the programmes you recorded have been.

---

### Post by Crusty Juggler on 2009-01-19
> **utar said:**
> I would guess you have the "live-tv" filter selected in show recordings rather then "default" which will show you the recordings.

I forget the key to change filters as these are all mapped on my remote, try pressing the the right arrow key a few times or m.

You can also check /var/lib/mythtv/recordings to see if the programmes you recorded have been.

That was it.  I went to "Watch Recordings" and hit "M" on the keyboard and got the menu to select "Default" instead of "Live TV," and that did the trick.  I knew it was something minor.  Thanks.

---

