---
title: "How do I install the Java Firefox plugin?"
date: 2009-07-04
forum: Multimedia Software
---

### Post by jim.hatley.tech on 2009-07-04
Hi all,

I am desperate to play Minecraft (I find it strangely addictive...), but I don't have the Java plugin installed in Firefox. The offer to install the Java plugin popped up when I tried to upload photos in Facebook, but I decided to try out IcedTea instead. IcedTea didn't work for Minecraft, but now I can't find any way to get the Java plugin installed. Am I being really dumb here guys? Any help would be well appreciated...

---

### Post by sdlynx on 2009-07-04
open up Synaptics Package Manager and search IcedTea and uninstall it.  Then Firefox should detect you have no plugin for java and this time select the real Java plugin.

---

### Post by jim.hatley.tech on 2009-07-05
Hey man, I tried that but no dice. Now I get no Minecraft or photo uploads, and no popup to tell me that a plugin is missing. I followed instructions I found elsewhere telling me to make a symbolic link for the i386 JRE plugin into the Firefox plugin folder, which I did with > ln -s but still no joy. Why doesn't Firefox include support for this as standard I wonder...

---

### Post by anystupidname on 2009-07-06
This not do anything for you?
```
sudo aptitude reinstall sun-java6-plugin
```

---

