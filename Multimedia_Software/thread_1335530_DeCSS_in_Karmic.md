---
title: "DeCSS in Karmic"
date: 2009-11-23
forum: Multimedia Software
---

### Post by Black Razor on 2009-11-23
Can someone please tell me how to install DeCSS in Karmic?  I've been searching threads for days and can't find any command line prompts that work anymore. Anyone?

---

### Post by mc4man on 2009-11-23
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh
```

The libdvdread4 install make be redundant (already installed), doesn't matter ( just want to make sure the .sh is present

---

### Post by Black Razor on 2009-11-23
You ROCK Mc4Man! Thanks a bunch.

---

