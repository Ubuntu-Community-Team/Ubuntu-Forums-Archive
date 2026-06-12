---
title: "change language in VLC player!"
date: 2011-03-16
forum: Multimedia Software
---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-16
my VLC player is a language i cant understand, i try to do ```
vlc --language=en
```but it dident work

---

### Post by gyussz on 2011-03-16
Try:
```
LANGUAGE=en vlc
```
There's no language selector in VLC tho, and I think it is auto-detecting the language from the locales of your operating system. It must be a bug that it's in a language you don't really know. You might need to change the Launcher in the main menu (or on the desktop) if you don't want to reconfigure locales.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-16
yes that worked, thanks
the language that was autodetected was norwegian but "nynorsk" not the norwegian i speak, so i dident understand it lol

btw do you know how i can do so the program will be english automaticly every time i open it? because i tried to close vlc and reopen it again and it was back to that "nynorsk" language... i tried to do the right click on "programs" and "edit menys" and put the both commands inside there but it dident work

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-22
Bump!:D

---

### Post by gyussz on 2011-03-22
Could you post the output of the following commands?
```
locale
```
```
cat /etc/default/locale
```

EDIT: Check the settings in System -> Administration -> Language Support choose the language you want, and Apply System-Wide. You may need a restart after this

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-24
```
LANG=nb_NO.utf8
LANGUAGE=nb_NO:nb:no_NO:no:nn_NO:nn:en
LC_CTYPE="nb_NO.utf8"
LC_NUMERIC="nb_NO.utf8"
LC_TIME="nb_NO.utf8"
LC_COLLATE="nb_NO.utf8"
LC_MONETARY="nb_NO.utf8"
LC_MESSAGES="nb_NO.utf8"
LC_PAPER="nb_NO.utf8"
LC_NAME="nb_NO.utf8"
LC_ADDRESS="nb_NO.utf8"
LC_TELEPHONE="nb_NO.utf8"
LC_MEASUREMENT="nb_NO.utf8"
LC_IDENTIFICATION="nb_NO.utf8"
LC_ALL=
```

```
LANG="nb_NO.UTF-8"
LANGUAGE="nb_NO:nb:no_NO:no:nn_NO:nn:en"
```

---

### Post by gyussz on 2011-03-24
Well, I guess VLC only have that mentioned "nynorsk" language for the Norwegian local. I Can't be sure. Best solution would be to change its Launcher. 

If you find an other solution feel free to share :)

---

