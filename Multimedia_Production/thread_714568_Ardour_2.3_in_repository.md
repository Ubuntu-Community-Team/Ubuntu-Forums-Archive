---
title: "Ardour 2.3 in repository?"
date: 2008-03-03
forum: Multimedia Production
---

### Post by dahouse on 2008-03-03
Hey guys,

I just checked out Ardour on the Ubuntu Repo and the version is 6months out of date. The version availablein the repo is 2.1 but the newest version offered is 2.3. Is there anyway to install version 2.3 via the repositories? I would build it from source but it doesn't offer a checkinstall version and I want it to be controlled via the Package Manager (you need to use SCons to compile and install it, whatever that is) and I want it to pop up in the menu.

I noticed the Hardy repo has version 2.3, is it possible to install from that?

---

### Post by Stochastic on 2008-03-03
The answer is yes - it is possible, but it's not recommended! The repositories should not be mixed (which is what you'd need to do to get ardour2.3 into your gutsy system through the repos).  If you start mixing packages from different versions of Ubuntu you will break things - the system is designed and checked as a whole.  Probably the reason why 2.1 is still in Gutsy and has not been upgraded to 2.3 is because of the other pieces of the puzzle needed to get everything running in 2.3.  Either install Hardy (and with it ardour), compile ardour from source, or stay with 2.1.

For myself, I don't mind waiting two months for Hardy  to come out (and with it, the current ardour).  And if you don't want to build ardour from source, that's what I'd recommend for you too.  Besides two months isn't that long.

Edit: it's actually more like a month and a half - which is even better!

---

