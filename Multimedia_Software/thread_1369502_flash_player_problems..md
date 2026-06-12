---
title: "flash player problems."
date: 2010-01-01
forum: Multimedia Software
---

### Post by Ganjafreak on 2010-01-01
I have got a new computer today, It's got most new parts in it but I installed all diffrent types of flashplayers, SMF players all that and I still can't play flash or watch videos. Anyhelp?

---

### Post by zg2pro on 2010-01-01
Hi Ganjafreak,

There is actually a bunch of packets on ubuntu for flash. I'm on ubuntu for a very long time and always upgrade my distrib, very often after the upgrade the problem of flash comes: if the new packet you use for flash doesn't corresponds exactly to the new version of your browser.

Generally the solution is not to install all the packets of flash you will find, believe me only one is enough. Actually what I recommend is you uninstall them all, and if your web browser is not too bad, you can install your flash plugin directly from there.

---

### Post by Ganjafreak on 2010-01-01
Okay, how do I unistall them?

And, I'm using google chrome, I even checked out Firefox and it still wouldn't do it.

---

### Post by inclusivedisjunction on 2010-01-01
I don't know what all packages you have installed to try to supply Flash, and if you used something outside the package manager, it could be a real mess. Try

```
sudo apt-get remove gnash
sudo apt-get install flashplugin-nonfree
```

You'll need to restart your browser before the changes will take effect.

---

### Post by ububaba on 2010-01-01
Very true about timing of the problem cropping up. However,
in my experience installing directly from the browser is not always
helpful.  

[HTML]sudo apt-get remove gnash
sudo apt-get install flashplugin-nonfree[/HTML]

Removing gnash was not much help either. I thought I had learnt something
about Ubuntu after using it for a long enough period. 

There is a solution out there. Where?

> **zg2pro said:**
> Hi Ganjafreak,

There is actually a bunch of packets on ubuntu for flash. I'm on ubuntu for a very long time and always upgrade my distrib, very often after the upgrade the problem of flash comes: if the new packet you use for flash doesn't corresponds exactly to the new version of your browser.

Generally the solution is not to install all the packets of flash you will find, believe me only one is enough. Actually what I recommend is you uninstall them all, and if your web browser is not too bad, you can install your flash plugin directly from there.

---

### Post by Ganjafreak on 2010-01-02
I already fixed this, I removed the swfdec player for mozilla and chrome, Then I installed a libdec or something like that player and it worked.

---

