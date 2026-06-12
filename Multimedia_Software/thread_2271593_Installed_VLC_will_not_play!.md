---
title: "Installed VLC will not play!"
date: 2015-03-31
forum: Multimedia Software
---

### Post by Victor_Gilbert on 2015-03-31
On a reinstalled Ubuntu 14.04 I installed VLC through the Software Centre plus the 3 codecs. I checked on the Terminal and it showed I have the latest VLC installed.

Strangely a friend gave me a video he made and it played it,** but **when I put a commercial DVD in it prepares to play but won't!

What am I missing?

Victor

---

### Post by TheFu on 2015-03-31
Commercial DVDs have encryption. You need to load the decryption library.  VLC doesn't use any external codecs which is why it is so nice and bad. Depends on your point of view.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) explains.

---

### Post by slickymaster on 2015-03-31
To play commercial DVDs in Ubuntu you need to install **libdvdcss** for recognizing them, **libdvdread4** for reading them and **libdvdnav4** for navigating them. These are not included by default, because Canonical would have to pay a royalty, making Ubuntu non-free. For personal use however, they are free for you to install.

In a terminal window run```
sudo apt-get install libdvdcss libdvdread4 libdvdnav4
```Afterwards, and again in terminal run```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Rebooting might be necessary.

---

### Post by Victor_Gilbert on 2015-03-31
Thanks Slickymaster

Great - did the trick.

Victor

---

### Post by slickymaster on 2015-03-31
You're welcome.

Happy *buntuing.

---

