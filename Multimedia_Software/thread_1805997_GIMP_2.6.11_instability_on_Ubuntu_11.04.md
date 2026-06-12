---
title: "GIMP 2.6.11 instability on Ubuntu 11.04"
date: 2011-07-17
forum: Multimedia Software
---

### Post by tomdkat on 2011-07-17
Has anyone else running Ubuntu 11.04, either 32-bit or 64-bit, experienced issues running GIMP?  I've been running into a number, such as:
[list]
[*]Taking a screenshot from within GIMP hangs the system such that manually powering off the system is the only way to recover
[*]The Bevel and Emboss plugins in the "FX-Foundry" don't work
[*]A number of scrollable fields in various dialog boxes won't scroll due to the "condensed", I guess, scrollbar
[/list]
I'm not running Unity since that won't run on my system for whatever reason. I'm running 64-bit Ubuntu with the classic GNOME interface.

Has anyone else experienced instability in GIMP on Ubuntu 11.04?

Thanks in advance!

Peace...

---

### Post by a1an on 2011-09-05
Yes, on my 32 bit system it hangs on startup when "Looking for data files". Tried a reinstall with no success so I have no way of starting it in 11.04. I guess its more than some instability here.

Regards

---

### Post by a1an on 2011-09-05
I removed everything related to gimp after an update to gimp 2.7 using the svn repositories: ppa:matthaeus123/mrw-gimp-svn taken from this guide: [http://www.multimediaboom.com/top-10-things-to-do-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://www.multimediaboom.com/top-10-things-to-do-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Then I reinstalled everything after removing the svn repository to get back to 2.6. There were two "missing" libraries that needed remove and install:  libbabl-0.0-0 and libgegl-0.0-0

Now it works again!

---

### Post by tomdkat on 2011-09-23
Cool, thanks for the info. Does the system hang (or the X server at least) if you take a screenshot from within GIMP itself?

Peace...

---

### Post by a1an on 2011-09-26
Now, after reinstalling, taking a screenshot within GIMP (2.6.11) works without problems. I did not try it before reinstalling since I was even unable to start it.

---

### Post by tomdkat on 2011-12-12
> **tomdkat said:**
> 
[list]
[*]Taking a screenshot from within GIMP hangs the system such that manually powering off the system is the only way to recover
[*]The Bevel and Emboss plugins in the "FX-Foundry" don't work
[*]A number of scrollable fields in various dialog boxes won't scroll due to the "condensed", I guess, scrollbar
[/list]
Well, these issues have all gone away after upgrading to Ubuntu 11.10 and Unity.  :)

Peace...

---

