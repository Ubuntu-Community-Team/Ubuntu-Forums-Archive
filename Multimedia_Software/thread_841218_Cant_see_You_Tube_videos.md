---
title: "Cant see You Tube videos"
date: 2008-06-26
forum: Multimedia Software
---

### Post by gurveentaneja on 2008-06-26
Im using xubuntu as my operating system and windows vista along with it......I cant see you tube videos on xubuntu but can do that in vista......I have my sytem up to date by installing all updates through update manager.........the browser also is not showing any plugins to be installed.........what should i do???

---

### Post by Canis familiaris on 2008-06-26
Go to Applications->Add Remove.
In the show option box select All Available applications
Search for flash and install Macromedia Flash Plugin

EDIT: Oh you are using Xubuntu.
Then go the terminal (Alt+f2->xterm)
and enter command:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by wormser on 2008-06-26
Do you have Flash installed?  Check for the package flashplugin-nonfree.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Canis familiaris on 2008-06-26
I would strongly suggest to enter this command as this will install Flash, Java, as well as codecs for mp3, mpeg videos, etc.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Canis familiaris on 2008-06-26
BTW why are using Xfce if your laptop can run Vista? I'm sure GNOME will run good as well. Ignore this post if Xfce is your preferred desktop environment.

---

### Post by gurveentaneja on 2008-06-26
> **Anurag_panda said:**
> BTW why are using Xfce if your laptop can run Vista? I'm sure GNOME will run good as well. Ignore this post if Xfce is your preferred desktop environment.

I am learning php that is why..

---

