---
title: "Can't ./configure mplayer rc2"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by 01000111 on 2008-02-27
Help... I'm trying to install the latest version of mplayer on Xubuntu v7.10 AMD64 and its a complete failure. I've only been Xubuntu-ing for a few months, so simple instructions please. It seems to say that my processors don't support the needed instruction sets, but that doesn't sound right to me. Any assistance is appreciated.

Thanks,
01000111


configure.log attached.

---

### Post by lloyd_b on 2008-02-27
> **01000111 said:**
> Help... I'm trying to install the latest version of mplayer on Xubuntu v7.10 AMD64 and its a complete failure. I've only been Xubuntu-ing for a few months, so simple instructions please. It seems to say that my processors don't support the needed instruction sets, but that doesn't sound right to me. Any assistance is appreciated.

Thanks,
01000111


configure.log attached.

Actually, those failures look more like a missing header file ("/usr/include/signal.h" to be specific) is the culprit.

Try installing the "build-essential" package:
```
sudo apt-get install build-essential
```
in a terminal window, or via the package manager of your choice (Syntaptic, Adept, etc).

With any luck, that will clear up everything.

Lloyd B.

---

### Post by 01000111 on 2008-02-27
That did it.  Thanks.

---

