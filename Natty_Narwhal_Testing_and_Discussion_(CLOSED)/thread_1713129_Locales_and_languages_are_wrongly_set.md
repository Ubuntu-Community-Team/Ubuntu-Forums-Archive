---
title: "Locales and languages are wrongly set"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MikeHunt on 2011-03-23
'Messed up' sounds a bit more accurate.
Ok, so maybe this will explain almost everything. I'm from Poland, I want my system to be in Polish but Gnome Language Support will never allow me to do so.
```
$ locale 
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=pl
LANGUAGE=pl:en
LC_CTYPE="pl"
LC_NUMERIC="pl"
LC_TIME="pl"
LC_COLLATE="pl"
LC_MONETARY="pl"
LC_MESSAGES="pl"
LC_PAPER="pl"
LC_NAME="pl"
LC_ADDRESS="pl"
LC_TELEPHONE="pl"
LC_MEASUREMENT="pl"
LC_IDENTIFICATION="pl"
LC_ALL=
$ locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
POSIX
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
pl_PL.utf8
```
This is the config I get every single time I restart system. It was freshly installed today after it became completely useless because of some kind of data corruption my Windows was proud to make.
Screen from the program itself: [http://i52.tinypic.com/28l73mq.jpg](http://i52.tinypic.com/28l73mq.jpg)
I also get loads of errors when installing or removing software.

Any help shall be appreciated. :D

---

### Post by Raubsau on 2011-04-03
Same here with German...

Did you let the installer download language packages?

Have you tried to remove Polish from the installed languages?


Please remove Polish via Language Selector.

Then start Ubuntu Software Center, search for "polish" and install all the language-packs.

Worked for me.

---

### Post by mpnordland on 2011-04-28
I have a similar problem, only with English. I upgraded to 11.04 from maverick and emerald won't work because the locale is set incorrectly.

---

### Post by dino99 on 2011-04-28
try "localepurge" from synaptic and/or gconf-editor

---

