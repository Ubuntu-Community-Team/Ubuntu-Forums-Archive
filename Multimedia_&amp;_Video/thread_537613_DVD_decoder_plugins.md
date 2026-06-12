---
title: "DVD decoder plugins"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by abhilash82 on 2007-08-29
How can I make DVDs to play in Totem or gxine players? CAn anyone give me the names of the suitable packages I have to install for DVDs to run?
:guitar:

---

### Post by Steve1961 on 2007-08-29
install libdvdcss2, w32codecs, and any gstreamer 10 plugins you might need

---

### Post by amgat on 2007-08-29
Enable universe and possibly multiverse repositories first!

```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Install xine backend for Totem

```
sudo apt-get install totem-xine
```

Finish installing modules: 

```
sudo apt-get install libdvdcss
```

---

### Post by MozartlovesUbun2 on 2007-11-09
> **amgat said:**
> Enable universe and possibly multiverse repositories first!

```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Install xine backend for Totem

```
sudo apt-get install totem-xine
```

Finish installing modules: 

```
sudo apt-get install libdvdcss
```

hi

i installed libdvdread from synaptics package manager

do i still have to run the sudo install-css.sh code in the terminal?

thx

---

