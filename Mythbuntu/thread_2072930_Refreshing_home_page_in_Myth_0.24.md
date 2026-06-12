---
title: "Refreshing home page in Myth 0.24"
date: 2012-10-18
forum: Mythbuntu
---

### Post by titan24 on 2012-10-18
I apologize if this has been asked but if the answers are around, I can't seem to find the right keywords.

My mythtv theme has indoor and outdoor temperatures displayed on the home page and in the pause osd.  

The problem I have is that the homepage of mythtv never gets reloaded.  Is there a way to make this page reload without closing and reopening the programme? (temp updates every 5 mins) .

Thanks

---

### Post by nickrout on 2012-10-19
> **titan24 said:**
> I apologize if this has been asked but if the answers are around, I can't seem to find the right keywords.

My mythtv theme has indoor and outdoor temperatures displayed on the home page and in the pause osd.  

The problem I have is that the homepage of mythtv never gets reloaded.  Is there a way to make this page reload without closing and reopening the programme? (temp updates every 5 mins) .

ThanksI assume you mean the main menu, as opposed to the "home page"?

What happens if you go into a sub menu and back out to the main menu?

By the way, you are two releases behind current. Support for 0.24 will dry up soon...

---

### Post by titan24 on 2012-10-19
Yes, main menu is correct.

> What happens if you go into a sub menu and back out to the main menu?

Nothing happens.  The mythtv manuals say that the main menu is the only "page" that never gets reloaded.  So when developing a theme, you need to close and reopen the frontend to check your progress.   They suggest adding code to a hotkey but don't elaborate... and I can't find anyone else who has done it yet.

> By the way, you are two releases behind current. Support for 0.24 will dry up soon... 	

I am hindered as are many by the "wife variable" which must be taken into account.   I have .25 on a partition but it is not at a level I would let my wife loose on yet.  There are also a lot of quirky extras I've added to my theme that need testing and fixing in 0.25

---

### Post by nickrout on 2012-10-20
Why don't you write a script to put the info on screen via mythutil and bind the script to a remote button.

---

### Post by titan24 on 2012-10-20
Is mythutil available in 0.24?  I thought it was new in 0.25.

---

