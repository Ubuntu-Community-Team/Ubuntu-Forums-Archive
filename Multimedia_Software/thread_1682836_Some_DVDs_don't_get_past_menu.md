---
title: "Some DVDs don't get past menu"
date: 2011-02-06
forum: Multimedia Software
---

### Post by DavidS on 2011-02-06
I have a new computer running Ubuntu 10.10.  I have VLC and Totem installed.  I am finding that a few DVDs, which played perfectly well on my old machine (running 9.10 most recently) now only show a first menu (language choice) but won't go on to show anything else.  Yet the majority of DVDs I have tried seem to be OK.

It isn't a region thing, because all of my DVDs except one are Region2 (or whatever the UK comes under), and the one exception is an American one, which also works fine.

David

---

### Post by coffeecat on 2011-02-06
Bit of a long shot this, seeing as you say that the majority of DVDs you've tried play OK, but have you installed libdvdcss2? You need this library for decrypting content scrambling of commercial DVDs. Either add the Medibuntu repo...

[http://www.medibuntu.org/](http://www.medibuntu.org/)

.. and install it with your package manager. Or run this command:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by DavidS on 2011-02-06
Thanks for the suggestion - but libdvdcss2 is already installed.

David

---

### Post by mc4man on 2011-02-06
There are some titles that due to the structure protection used can create an issue for players trying to navigate from the main menu to the movie.
In some of those cases pointing the player to the main movie title # will allow playback. (not something totem (gstreamer) is very good at doing.

---

### Post by DavidS on 2011-02-09
Probably very stupid of me, but I hadn't realized that in VNC I need to press Enter (activate) after choosing the language.  I was trying to select the language and move on using the mouse, but a double click merely maximises the window.  I discovered by accident that pressing Enter allows the DVD to go to the next stage.

Thanks for all the suggestions.

David

---

