---
title: "Submit entry to freedb with Grip"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by alainhenry on 2007-08-30
I am using grip to  rip and encode CD's.  In a few cases, the cddb freedb.org does not have info on the CD's and I'd like to submit the info to Freedb using Grip.  I click on the submit button (the envelope at the bottom right of the Grip screen).  Unfirtunately, nothing happens: no message, no update of the DB.  
The configuration parameters already include the correct e-mail for freedb submission.
Suggestion anyone ? Thanks in advance
Alain

---

### Post by alainhenry on 2007-10-08
Solved
I used KsCD and it allowed me to submit disc information to freedb.

---

### Post by gerv on 2008-03-09
According to this bug: [https://bugs.launchpad.net/ubuntu/+source/grip/+bug/32483/](https://bugs.launchpad.net/ubuntu/+source/grip/+bug/32483/) you need to have sendmail installed and correctly configured. This is hard-coded in grip; it can't be changed. :-( So either you need to set up a working sendmail (or some work-alike) or use a different submission program. :-((

Gerv

---

