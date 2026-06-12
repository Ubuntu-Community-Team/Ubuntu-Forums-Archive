---
title: "Adobe Air and Tweetdeck"
date: 2010-01-03
forum: Multimedia Software
---

### Post by createsean on 2010-01-03
Hi,

Today is my first day with ubuntu and I'm trying to figure out how to install Adobe Air and TweetDeck but can't get anything to work at all.

Is there a guide somewhere to do this with Ubuntu 9.1?

---

### Post by Filippo on 2010-01-08
get it from  here:[http://get.adobe.com/air/](http://get.adobe.com/air/)

then on a terminal

```
chmod +x AdobeAIRInstaller.bin
sudo ./AdobeAIRInstaller.bin
```

done.

If you are on a 64bit system and you got this error :
> Error loading the runtime (libadobecertstore.so: cannot open shared object file: No such file or directory)

do
```
sudo cp /usr/lib/libadobecertstore.so /usr/lib32/
```

bye

Filippo

---

