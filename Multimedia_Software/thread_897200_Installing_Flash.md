---
title: "Installing Flash"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Ahmed Amr on 2008-08-21
i tried to install flash player for mozilla and every time i get this msg
```
NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.

```
can anybody please help i am novice to linux just installed it 2 days ago

---

### Post by tuxxy on 2008-08-21
To install flash you can install ubuntu-restricted-extras package which includes it

search for ubuntu-restricted-extras in synaptic or type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/8.04/internet/C/web-apps.html](https://help.ubuntu.com/8.04/internet/C/web-apps.html)

---

### Post by aysiu on 2008-08-21
Can you paste these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here?? The first command may take a few minutes to execute. Just be patient. ```
sudo updatedb
locate xpti.dat
```

---

### Post by Ahmed Amr on 2008-08-23
actually i tried the first solution it worked good for me thanx tuxxy. and thanks aysiu.
but the problem now is that videos on youtube is so slow specially when i try full screen

---

