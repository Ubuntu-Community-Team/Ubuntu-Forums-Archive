---
title: "Flash Plugin Not Working"
date: 2009-11-02
forum: Multimedia Software
---

### Post by CarlosinFL on 2009-11-02
I did a fresh install of 9.10 last week and installed the Adobe Flash plugin for Firefox and noticed that the plugin works fine but some things don't work. I can't login to Pandora or I can't select some Flash options menus from Hulu.

I know Flash is rending properly since I can watch Youtube videos however the menus and other things don't appear to be working.

Any thoughts?

---

### Post by karimruan on 2009-11-02
I had the same problem with 9.04. My solution was to uninstall all flash plugins, upgrade the system (which included the new firefox) and run:
```


sudo apt-get install flashplugin-nonfree

```


I don't know if that is relevant to karmic, or if you already have the newest firefox (I assume you have all the jaunty updates if you run karmic.

Which plugin are you using?

---

### Post by CarlosinFL on 2009-11-02
I never had an issue in 9.04, just 9.10.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sudo is already the newest version.
```

---

### Post by Uncle Spellbinder on 2009-11-02
Are you on 64 bit Karmic? Have Compiz (desktop effects) enabled? If so, disable desktop effects and all should be fine. There is a known issue with [Flash/64bit/Compiz](http://ubuntuforums.org/showpost.php?p=8220329&postcount=156).

---

### Post by karimruan on 2009-11-02
Wish I knew that 6 months ago before I reinstalled as 32 bit!

---

### Post by CarlosinFL on 2009-11-02
Yes and I believe I do have desktop effects enabled. It's not on high. I think it's set to normal. I will disable it. Thanks!

---

