---
title: "Weird Flash Issues"
date: 2010-07-01
forum: Multimedia Software
---

### Post by eccapants on 2010-07-01
Here's my issue: A few days ago I upgraded from Karmic to Lucid. Everything seemed to have gone well and all was working. 
Then flash magically disappeared in firefox. I was able to restore it by uninstalling then reinstalling flashplugin-nonfree. The same thing happened roughly a day later. I've been doing the uninstall/reinstall for the past few days each time flash decides to die on me but today this fix didn't work. I've played around with various things and installed FLASH-AID. Now I have flash in* almost *everything (youtube is working again but surfthechannel is still non-functional). 
Any ideas what the problem is and how I could fix it?
Thanks!

---

### Post by lovinglinux on 2010-07-02
When the problem happens again, verify if flashplugin-installer is installed and if Firefox is detecting it.

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

If the package is installed, but Firefox doesn't recognize it, then you might have a problem with your user profile. Sometimes deleting **pluginreg.dat** from it helps, since forces Firefox to detect the plugins again.

---

