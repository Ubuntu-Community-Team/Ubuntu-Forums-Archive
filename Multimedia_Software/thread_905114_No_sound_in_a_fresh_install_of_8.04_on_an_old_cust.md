---
title: "No sound in a fresh install of 8.04 on an old custom built computer"
date: 2008-08-30
forum: Multimedia Software
---

### Post by maxbaroi on 2008-08-30
I came into an semi-old (about 4 years old) desktop computer recently and decided to swipe everything form the hard drive and install Ubuntu. But now I have no sound. 

The computer was custom built by a small computer store so I can't tell if it's Compaq, Dell, Gateway, etc. 

Here's the result of lspci -v | grep audio

```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

```

---

### Post by loboc on 2008-08-30
the snd-intel driver has been giving some people problems theres a howto to reinstall or reconfigure it floating around here on the forums sommwhere

---

### Post by loboc on 2008-08-30
This post has the bare minimum steps of trouble shooting a soundcard

[http://ubuntuforums.org/showpost.php?p=5638028&postcount=4](http://ubuntuforums.org/showpost.php?p=5638028&postcount=4)

---

### Post by maxbaroi on 2008-08-30
That didn't work for me.

---

