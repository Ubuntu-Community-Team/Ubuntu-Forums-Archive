---
title: "pyqt not found, installing thinliquidfilm"
date: 2010-03-14
forum: Multimedia Software
---

### Post by d4_user on 2010-03-14
```
~/thinliquidfilm$ sudo ./install.py
*************************************
      installing thinliquidfilm
*************************************


-------------------------
Checking dependencies ...
-------------------------

Couldn't find pyqt.  thin liquid film will not work without pyqt.  Aborting installation.

```

i did
```
~/thinliquidfilm$ sudo apt-get update
~/thinliquidfilm$ apt-cache search pyqt

```
and
```
~/thinliquidfilm$ sudo apt-get python-qt4
~/thinliquidfilm$ sudo apt-get install python-qt4-common

```
but it said it was already installed, no files changed or written.

why does it think pyqt isnt installed?

---

### Post by Yellow Pasque on 2010-03-14
```
sudo apt-get install python-qt4-dev
```

---

### Post by d4_user on 2010-03-15
i did it, but it still says pyqt not found.

```
-------------------------
Checking dependencies ...
-------------------------

Couldn't find pyqt.  thin liquid film will not work without pyqt.  Aborting installation.

```
=[

---

### Post by d4_user on 2010-03-15
I got it, i had to install python-qtext

---

### Post by afarenci on 2010-10-23
> **d4_user said:**
> I got it, i had to install python-qtext

It wasn't python-qtext that fixed the problem, it's python-qt3.

I had the same problem so I went to install python-qtext, but I noticed it was dependent on python-qt3, so I only installed that instead.  That got me through the pyqt error.

That got me to the broken script error (dash instead of bash) which is fixed with:
[INDENT][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**rm**[/COLOR] [COLOR=#660033]-f[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#C20CB9]**sh**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#C20CB9]**bash**[/COLOR] [COLOR=#000000]**/**[/COLOR]bin[COLOR=#000000]**/**[/COLOR][COLOR=#C20CB9][B]sh

[/B][/COLOR]

[/INDENT]Now it's just complaining that it can't find my kde directory
[COLOR=#C20CB9]****[/COLOR]
[COLOR=#C20CB9]****[/COLOR]

---

