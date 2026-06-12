---
title: "how do i get exaile to play off my cd-rom?"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by Pitt Stains on 2007-08-14
Having to ask this question makes me feel dumb, but I can't seem to get Exaile to play directly off my cd-rom.  I don't know where to navigate within the app to tell it to do so.  Anyone?

While we're on the subject, does anyone know how to change the default file handlers in Gnome?  Double-clicking an ogg vorbis file opens up Totem -- yuck!

In general I find the documentation for Exaile to be pretty incomplete.  I hear that you can rip/burn music from within Exaile too, but again, I have no idea how.

I think even setting up a user forum on Exaile.org would be a huge improvement...

---

### Post by 5-HT on 2007-08-14
Installing python-cddb should do the trick for getting CDs to play in exaile.
As to the default open-with handlers: navigate to the file type in question in Nautilus, right-click, select properties, and there's an "open-with" tab.
cheers,

---

### Post by Pitt Stains on 2007-08-15
> **5-HT said:**
> Installing python-cddb should do the trick for getting CDs to play in exaile.

Thanks, but not quite.  It added an option for me in the menu (open disc), but when I click it nothing happens.  Any other suggestions?

---

### Post by 5-HT on 2007-08-20
This is what I'm using: [http://cddb-py.sourceforge.net/](http://cddb-py.sourceforge.net/)
I thought the Ubuntu package was the same, but it's not and this package unfortunately isn't in the repos. It's an easy compile though.
cheeers,

---

