---
title: "Rhythmbox artist view"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by knave on 2007-05-28
Hi guys,

First up, I love the forums.  I've been using Ubuntu Feisty since release and I'm lovin it.  I tried 5.10 but uninstalled it....I don't recall why, but I guess it's improved, because I'm still with it!  The forums have been a tremendous help, and I've learned a lot by searching...but not this one.

In Rhythmbox, I can't find out how to ignore the "The" when viewing albums and artists.  For example, I want "The Datsuns" to be located by "David Bowie" and not "Thom Yorke".

This is a tough one to search for!

Normally I wouldn't care too much, but Rhythmbox has done this to my iPod as well.  It's really annoying!


Any help would be much appreciated.

George.

---

### Post by knave on 2007-05-29
:-(

---

### Post by pertti on 2007-05-29
> **knave said:**
> In Rhythmbox, I can't find out how to ignore the "The" when viewing albums and artists.  For example, I want "The Datsuns" to be located by "David Bowie" and not "Thom Yorke".

This is a tough one to search for!

Normally I wouldn't care too much, but Rhythmbox has done this to my iPod as well.  It's really annoying!

There is a bug report for this here: [http://bugzilla.gnome.org/show_bug.cgi?id=133444](http://bugzilla.gnome.org/show_bug.cgi?id=133444). In short: there is no way to do it now, and it looks unlikely in the short term. The problem would be that "The" is an article in English, but it may be a regular word in other languages. Plus, Rhythmbox should also ignore the articles in other languages, such as "El" in Spanish.

As for the iPod thing, I've always used gtkpod and it sorts the artists ignoring the "The". You could try that, but gtkpod doesn't have a nice interface as Rhythmbox, and you'll have to mantain your music collection there aswell.

---

