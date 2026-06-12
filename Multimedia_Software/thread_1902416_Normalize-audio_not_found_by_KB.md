---
title: "Normalize-audio not found by KB"
date: 2011-12-30
forum: Multimedia Software
---

### Post by crazy bird on 2011-12-30
Hi,

I've installed normalize-audio for K3B and now i noticed that k3b cannot find this tool.

screenshot 1
[http://imageshack.us/photo/my-images/194/instellingenk3b00130122.png](http://imageshack.us/photo/my-images/194/instellingenk3b00130122.png)

screenshot 2
[http://imageshack.us/photo/my-images/155/instellingenk3b00130122.png/](http://imageshack.us/photo/my-images/155/instellingenk3b00130122.png/)

screenshot 3
[http://imageshack.us/photo/my-images/215/instellingenk3b00130122.png/](http://imageshack.us/photo/my-images/215/instellingenk3b00130122.png/)

screenshot 4
[http://imageshack.us/photo/my-images/600/selectie001301220112308.png/](http://imageshack.us/photo/my-images/600/selectie001301220112308.png/)

Screenshot  shows that normalize-audio is installed under ./usr/bin/.
Who has a solution?
Many thanks in advance!

---

### Post by mc4man on 2011-12-30
For RubyRipper, which looks for "normalize", not "normalize-audio", I do this, may be the same for k3b which I don't have installed

```
sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

Edit: I always put stuff I add or mod in either ~/ or /usr/local so the above assumes /usr/local/bin exists. I forget if it is there by default so a varition of above - 
```
sudo mkdir -p /usr/local/bin && \
sudo ln -s /usr/bin/normalize-audio /usr/local/bin/normalize
```

---

### Post by crazy bird on 2011-12-31
I found a solution later and put it [on my site]("https://sites.google.com/site/tipsandtricksforubuntu/system-tips/k3b-and-normalize-audio").

---

### Post by MoreOrLess on 2011-12-31
Please mark thread solved.

---

