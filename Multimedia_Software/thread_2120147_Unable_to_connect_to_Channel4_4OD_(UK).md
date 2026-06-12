---
title: "Unable to connect to Channel4 4OD (UK)"
date: 2013-02-25
forum: Multimedia Software
---

### Post by oxf on 2013-02-25
I am finding it impossible to connect to streaming video on the Channel4 On Demand site. This is happening in both Firefox and Chromium. Video on other sites eg BBC works fine so am I missing some package, codec etc? On a previous release of Ubuntu I had no problem so I don't know what the problem is?

Any sugestions? Thanks..

---

### Post by oxf on 2013-03-03
Investigating this a bit further I find that the same problem occures with Channel 5 which offers a similar archive type of thing to Channel 4 oD. It's not happeneing on many other sites such as BBC online etc.

Specifically it trys to connect to/load the video but noything happens, i.e. the circle thingy in the centreof the screen goes around and around.... and so on.

I suspect it has something to do with with adobe flash but I'm not sure. I do have flash installed (not flash installer though)
If any one has any ideas as I suspect it's something fairly simple missing.
Thanks

Caitlin

---

### Post by evilsoup on 2013-03-03
I'm sure this has come up before, and the solution posted was to install hal.

```

sudo apt-get install hal

```

...or you can probably get it from the software centre.

---

