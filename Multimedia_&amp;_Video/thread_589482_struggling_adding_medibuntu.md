---
title: "struggling adding medibuntu"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by applehead on 2007-10-24
Hi.
I'm following the instructions in the sticky 'Enabling Multimedia in Feisty (HOW-TO)'.
I'm trying to add medibuntu to the /etc/apt/sources.list file.

 Ive copied and pasted:
 $sudo vim /etc/apt/sources.list

then copyed and pasted:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

then copied and pasted 
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

then it says:
 gpg: no valid OpenPGP data found.
paul@paul-desktop:~$ 

I know I'm doing something very wrong, can anyone tell me what?

---

### Post by applehead on 2007-10-24
Please help, this is my last day off work!

---

### Post by RRS on 2007-10-24
```
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

These two lines worked for me on two different machines so far.

---

### Post by applehead on 2007-10-24
Thankyou that seems to work fine.
Three days that has took me and then less than a minute after your post.
So what was I doing wrong?

---

### Post by jespdj on 2007-10-24
Those instructions are on the medibuntu website on the "Repository Howto" page:
[http://www.medibuntu.org/](http://www.medibuntu.org/) then click "Repository Howto" -> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

So, what you did wrong was... you didn't look for the instructions in the most obvious place... :confused: ;)

---

### Post by Kingsfan on 2007-10-24
> **jespdj said:**
> Those instructions are on the medibuntu website on the "Repository Howto" page:
[http://www.medibuntu.org/](http://www.medibuntu.org/) then click "Repository Howto" -> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

So, what you did wrong was... you didn't look for the instructions in the most obvious place... :confused: ;)

the sticky should be updated, i tried the same thing til i found this thread, thanks for helping though! worked great

---

