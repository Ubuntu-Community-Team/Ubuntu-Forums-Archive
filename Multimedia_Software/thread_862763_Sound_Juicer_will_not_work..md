---
title: "Sound Juicer will not work."
date: 2008-07-17
forum: Multimedia Software
---

### Post by kaldor on 2008-07-17
I install it via Synaptic. It does not show up in multimedia. What can I do to fix it?

---

### Post by llama320 on 2008-07-17
On the menu, Sound Juicer is listed as Audio CD Extractor under Apps > Sound & Video

if you want to change the name, go to System > Preferences > Main Menu

Good Luck

---

### Post by kaldor on 2008-07-17
It will not load now. I click it, and it just has the timer, then disappears.

---

### Post by llama320 on 2008-07-17
if you run 
```
sound-juicer
```
from terminal, is there any output?

---

### Post by kaldor on 2008-07-17
nothing happened.

---

### Post by llama320 on 2008-07-17
all i can really offer is then to purge the file, autoremove, autoclean (making sure your  system is as it should be) and then reinstalling. Otherwise i'm not sure how to debug a problem that doesn't give any indication that it's having trouble..anyways, try this:

```
sudo apt-get purge sound-juicer
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install sound-juicer
```

Good Luck

---

### Post by ohgodnotanother1 on 2009-02-08
> **kaldor said:**
> It will not load now. I click it, and it just has the timer, then disappears.

It might sound odd, but I also had this during one system run. After the next boot-up the problem disappeared, so I don't know what was causing it - Sorry.

---

