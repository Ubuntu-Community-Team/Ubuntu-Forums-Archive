---
title: "Video interface of vlc is empty."
date: 2010-02-09
forum: Multimedia Software
---

### Post by hariks0 on 2010-02-09
Hi all, Vlc is no more able to play video. The video interface of vlc is transparent as you can see from the screenshot. The major change I made recently updation of Cair-dock to version 2.1.3-2 from ppa. VLC version is 1.0.3.

thank you for any help.

---

### Post by HappyFeet on 2010-02-09
Comletely remove vlc, then do 
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall vlc.

---

### Post by hariks0 on 2010-02-10
> **HappyFeet said:**
> Comletely remove vlc, then do 
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall vlc.

Did all this. but no luck.It is still empty. Media player works perfectly. But I like vlc thn any other.

---

### Post by mc4man on 2010-02-10
Either find or build yourself a newer vlc (1.0.4, 1.0.5 or a patched 1.0.3) or remove cairo-dock or read here ect.
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/416294](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/416294)

*I don't believe the korn ppa vlc 1.0.3 is patched for cairo, maybe try getdebs or elsewhere... if building isn't an option

---

