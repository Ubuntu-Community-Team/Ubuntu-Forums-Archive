---
title: "whats wrong with my internet?"
date: 2008-05-30
forum: Multimedia Software
---

### Post by helpineed on 2008-05-30
when i try to run flash or videos on my computer in firefox instead of just showing it to me firefox just puts a play sign there.when i click on it, it *sometimes* shows it to me though. How do i get rid of this irratating/annoying/distressing/depressing feature? :confused:

---

### Post by tamoneya on 2008-05-30
its probably some firefox extension that you have installed,  What are your current extensions?

---

### Post by helpineed on 2008-05-30
firefox says i have the Default Plugin, Demo Print Plugin,DivX Web player,HelixDNA Plugin, iTunes application detector, Quicktime plugin and 2 flashes.huh?

---

### Post by tamoneya on 2008-05-30
that seems fine.  Try removing and reinstall flashplugin-nonfree```
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by helpineed on 2008-05-30
still no luck

---

### Post by tamoneya on 2008-05-31
what happens if you try it with a different broswer.  Try opera.  If it isnt installed use this:```
sudo apt-get install opera
```Also im curious to know if you are using 32 or 64 bit.  64 bit causes complications with flash.

---

### Post by gandaran on 2008-05-31
that play sign is swfdec flash! go to synaptic, find swfdec and remove it completely, install the flashplugin-nonfree (adobe flash) if you haven't all-ready.

---

### Post by helpineed on 2008-05-31
Thanks gandaran! it works perfectly now :lolflag:

---

