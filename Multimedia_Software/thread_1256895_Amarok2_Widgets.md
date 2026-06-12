---
title: "Amarok2 Widgets"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Hatch3r on 2009-09-03
Morning all,
I recently switched over to Amarok2 from 1.4.10 and was playing around with the widgets. I added a couple and each one didn't work.
So I right clicked to remove it, and it won't. Nothing happens.
The widget itself appears as:
"This object could not be created for the following reason:
Could not find the requested component:"

I've since tried completely removing Amarok2 through Synaptic and reinstalling that didn't shift it. Though when I subsequently tried adding widgets they work fine (and can be removed).

Any ideas?

Regards

---

### Post by Hatch3r on 2009-09-05
Has anyone got any ideas on this?

---

### Post by Hatch3r on 2009-09-05
Fixed it. After finding the Amarok forum I had a quick search and lo and behold I found the solution;

From [here (Clicky)](http://forum.kde.org/viewtopic.php?f=115&t=73755&p=113932&hilit=Remove+unknown+widgets#p113932)
(I confess I skipped right to the bottom of the thread to see if the issue was resolved)
This was the information required:
> That didn't work.  However, I did some more searching and found that deleting the file ~.kde4/share/config/amarok_homerc did the trick.  It is hard to figure these things out when applications create so many configuration files.

On my system the path was: "~/.kde/share/config/amarok_homerc"

---

