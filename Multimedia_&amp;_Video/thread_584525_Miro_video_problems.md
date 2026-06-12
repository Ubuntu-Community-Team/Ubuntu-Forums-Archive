---
title: "Miro video problems"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by leetcharmer on 2007-10-21
Miro won't play .mov files in Gutsy.  How do I fix this?  They work in Totem.

---

### Post by papatrpt89 on 2007-10-23
I believe that Miro uses VLC as its backend.

That said, I have Miro installed and playing, with the package win32codecs (I think).  You have the install that from the medibuntu repository...

**Method 1:**From a terminal:
```
sudo apt-get install libxine1-plugins
```

**Method 2:**From a terminal:
```
gksu gedit /etc/apt/sources.list
```

Inside of gedit, add the following code to the end of the file:
```
deb http://packages.medibuntu.org/ gutsy free non-free
```

Add the GPG key to your keyring:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

From inside a terminal, update your package sources:
```
sudo apt-get update
```

Then, from inside a terminal, type:
```
sudo apt-get install w32codecs
```

If it gives you any authentication errors, you can ignore them.

Alternatively, if this isn't working for you, try installing VLC from the repositories, along with any good looking plugins.

Good luck!

---

