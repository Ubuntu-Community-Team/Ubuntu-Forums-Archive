---
title: "PureData and GEM"
date: 2008-04-07
forum: Multimedia Production
---

### Post by robeast on 2008-04-07
I just did some searching around the internet and these forums looking for the proper way to start up PureData with the GEM libraries. Since I couldn't find any accurate info on this I had to figure it out myself. I figure I should throw it up here so if others have the same problem they may find this thread.

Open the terminal and do this:
```
$ pd -lib /usr/lib/pd/extra/Gem
```

or open PD with its graphical icon, select File >> Startup... and paste "/usr/lib/pd/extra/Gem" (minus quotes) in one of the boxes.

---

