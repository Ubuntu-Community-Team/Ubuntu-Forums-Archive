---
title: "[SOLVED] Cannot play new DVDs"
date: 2008-12-25
forum: Multimedia Software
---

### Post by k3lt01 on 2008-12-25
I have a minor problem in that I am unable to play any new DVDs on my Ubuntu machines. They will play on my families Windows machines but not on my Ubuntu desktop or laptop. My machines have the latest Ubuntu, Canonical, and MediBuntu repositories updated. I have tried to read them in k9copy and view them in Movie Player. I get a message saying unable to read from source. I know its not my disk drives because they will play older DVDs.

I'm hoping someone can help me with this problem.
Thanks in advance.

EDIT: It pays to be patient. I have had this trouble for days yet 15 minutes after I post about it I fix it myself. I uninstalled Media Player (Totem) completely and everything in it and then reinstalled it all again. I have done this a couple of times before but this time it worked.

---

### Post by lavinog on 2008-12-29
See if VLC works
edit: also you should install libdvdcss
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
if you get a file not found error, make sure you have libdvdcss2 installed in synaptic

---

### Post by k3lt01 on 2008-12-29
lavinog, did you notice I had already fixed it?

---

