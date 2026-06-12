---
title: "Jokosher not picking up LADSPA plugins"
date: 2010-10-04
forum: Multimedia Software
---

### Post by slackthumbz on 2010-10-04
Title pretty much says it all, I've installed just about every ladspa plugin package I can find but jokosher just can't find 'em. Audacity, LMMS, Ardour etc all detect them without fail. Anyone had the same problem and found a working solution?

SOLVED: You need to force the registry to re-load, you can do this by deleting your .gstreamer-0.10 dir

rm -rf ~/.gstreamer-0.10

---

