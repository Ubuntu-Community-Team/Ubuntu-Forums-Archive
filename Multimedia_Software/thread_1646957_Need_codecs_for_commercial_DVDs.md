---
title: "Need codecs for commercial DVDs"
date: 2010-12-16
forum: Multimedia Software
---

### Post by parl8256 on 2010-12-16
I am unable to play commercial DVDs on an Ubuntu laptop.

I have a fairly new Lenovo 4151 laptop. It came with Windows 7 Premium but I have replaced that with Ubuntu 10.04 LTS Lucid. (Actually, a friend helped me do that.) I would like to play commercial DVD's on it.

Movie Player says it need a plugin but is unable to find on on the web. "No packages with the requested plugins found." "The requested plugins are: DVD Source"

So I installed VLC Media Player and it won't play the DVD either. It presents me with a host of files, none of which it will play.

I would like to stay with 10.04 if possible because I want to give this lap-top to my sister and I would like her to have an LTS distro, so she doesn't have to upgrade for a long time.

My supposition is that I need to add a source for additional codecs and install them.

I did search these forums (fora?) for codec, but didn't find anything appropriate. I'm not so familiar with this, so I may have missed something. If so, I apologize. Just let me know how to find it and I'll go there to look. Thanks.

Ross

---

### Post by wojox on 2010-12-16
Try

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Reboot. [Source...]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by trinitydan on 2010-12-16
Edited out...  Should have read OP more carefully..

---

