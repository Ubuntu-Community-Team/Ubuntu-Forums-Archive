---
title: "Konqueror YouTube Layout Problems."
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by teolandon on 2011-03-25
So, I switched to KDE a couple of weeks ago, and I find it pretty good. I tried Konqueror and it turned out to be a really faster browser than Firefox. But I have a problem. When I go to YouTube, the layout is a little messed up: [http://i56.tinypic.com/2imarna.png](http://i56.tinypic.com/2imarna.png)

(I blurred my username, just in case...)

This also happens with some other websites.

Any way to fix that?

---

### Post by kio_http on 2011-04-03
Try switching konqueror to the webkit backed.

```
sudo apt-get install kpart-webkit
```
```
keditfiletype text/html
```

Go to the Embedding tap and under the Service Preference Order option, click on WebKit and move it to the top.

---

