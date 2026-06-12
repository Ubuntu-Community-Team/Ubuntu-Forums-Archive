---
title: "Gnome Panels Gone"
date: 2010-07-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sgage on 2010-07-30
I just did the latest updates (~4:30 p.m. EDT US). My networking stopped working, and I couldn't get it going, so I thought I'd reboot to see if it would come to its senses. I rebooted, and no panels, neither top nor bottom. What to do?

---

### Post by MacUntu on 2010-07-30
Well, you probably uninstalled a bunch of packages like I just did.

Always check for packages listed for removal! :>

---

### Post by sgage on 2010-07-30
Was pretty sure I didn't remove any packages - I always check the bill of goods before I "apply changes". But mabye I got lax this time. Oh well. I will see if I can recover...

---

### Post by MacUntu on 2010-07-30
Just check if you have gnome-panel installed - I don't, but fortunately I haven't rebooted. :P

```
The following packages have unmet dependencies:
 ubuntu-desktop : Depends: software-properties-gtk but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: ubufox but it is not going to be installed
```

:(

Half an hour ago it was a lot more, so I think it soon will be ok. :)

---

### Post by sgage on 2010-07-30
Yes, looking at the history log, I had removed a LOT of packages... I usually catch that beforehand. Oh well! Live and learn... I'll wait a while and try to apt-get install ubuntu-desktop.

---

### Post by sgage on 2010-07-30
Back in the saddle! 

That was the first time in a long time I've been bitten by not noticing a large list of "to be removed"  :p

---

