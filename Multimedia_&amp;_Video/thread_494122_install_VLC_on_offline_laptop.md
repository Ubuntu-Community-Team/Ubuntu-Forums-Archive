---
title: "install VLC on offline laptop?"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by ronniet on 2007-07-06
I know I can easily install **VLC** from the repo's but I can't get online with my laptop in work (no wireless connection). Is there an easy way to install VLC without the repo's? Like a *.deb *file?

My laptop only has the basic Ubuntu install on it, nothing fancy so doubt it can compile source or anything...

Any help would be moooost welcome!

***Ta much!***

---

### Post by paulg on 2007-07-06
You should be able download the deb from a repository (search/browse one, try packages.ubuntu.com). If you can get on a CD or media stick you can install it. To install: ```
sudo dpkg -i vlc*.deb
```

---

### Post by kerry_s on 2007-07-06
easy way, no! vlc has a ton of dependency's. 
off line you should go with mplayer and the w32codecs.

---

### Post by xfile087 on 2007-07-06
> **paulg said:**
> You should be able download the deb from a repository (search/browse one, try packages.ubuntu.com). If you can get on a CD or media stick you can install it. To install: ```
sudo dpkg -i vlc*.deb
```

Also a similar idea is to use aptoncd - it will make a backup of all your packages (you can pick and choose what to include when making or re-installing) to CD so that you can then take it to your laptop and re-install them all on there. I've done this with my desktop/laptop and works perfectly!

---

