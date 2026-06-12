---
title: "Embedded videos won't play"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by siegfre on 2007-06-07
I'm running Ubuntu 7.0.4 w/ Totem Movie Player.  When I try to view a website with an embedded video Totem gives me a pop-up that says "Could not open location; You may not have permission to open the file".  This only happens w/ video files that have blanks in the name.

---

### Post by crispy_420 on 2007-06-08
Did you try mplayer and browser plugin?

---

### Post by Gwasanaethau on 2007-06-08
> **crispy_420 said:**
> Did you try mplayer and browser plugin?

I couldn't use totem-mozilla plugin at all. I removed it using:
```
sudo apt-get remove totem-mozilla
```
and installed mplayer using:
```
sudo apt-get install mozilla-mplayer
```
NB: This will install mplayer and all its required files too. Under Edgy I was able to use the 'no-GUI' version with the plugin (which I preferred), but under Feisty it seems you have to install the full GUI version.

---

### Post by Bablefish on 2007-06-08
Common problem the fix is simple and it doesn't matter which player you use. Once you get Medibuntu installed I reccomend the terminal install found on the Medibuntu site go here: [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Once you run it, you'll be able to run just about everything

---

