---
title: "How Do I Keep My ALSA Drivers Working?"
date: 2010-01-09
forum: Multimedia Software
---

### Post by mulluysavage on 2010-01-09
Running songbird, have been just fine for months, now every time I try to play a file I get "autoaudiosink and alsasink are missing." I can cure this by following the "Getting the ALSA drivers from a *fresh* kernel" instructions in the comprehensive sound solutions guide. But I have to do this *every time* I restart my computer. How can I fix this permanently?

---

### Post by lidex on 2010-01-10
You can try this alsa update procedure:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by mulluysavage on 2010-01-10
on sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
I get "Make failed."

Mythbuntu (xfce) install
Ubunti 8.04 lts
upgrading from ALSA 1.0.16

---

### Post by lidex on 2010-01-10
What is your output of this command:
```
uname -a
```

You were able to get through step 4, I take it?

More resources here:
[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

---

### Post by mulluysavage on 2010-01-10
Linux mediabot 2.6.24-26-generic #1 SMP Tue Dec 1 18:37:31 UTC 2009 i686 GNU/Linux

yes was able to get through step 4

---

