---
title: "language support not working?!"
date: 2010-08-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sartic on 2010-08-30
I am stuck width english. Grrrr
Policykit bug or more than that?

---

### Post by Kobalt on 2010-08-30
Which language are you trying to use? 
Did you install the language support packages?
What's the status of your language's translation on Launchpad?

---

### Post by sartic on 2010-09-01
croatian, i will wait final.

---

### Post by Lollerke on 2010-09-01
+1, installed the aug 28th daily live and installing languages doesn't work ( in ubiquity and in the language support menu too). I had to install the language packages manually in Synaptic.

---

### Post by vulture on 2010-09-18
Until gnome-language-selector gets fixed in final, i fixed language selector this way:

open with text editor as root:
```
gksudo gedit /usr/lib/python2.6/dist-packages/LanguageSelector/utils.py
```

then change line 36:
```
os.rename(out.name, fname)
```

to:
```
os.system("mv %s %s" % (out.name, fname))
```

os.rename is method for renaming files, for some odd reason this is broken in maverick (raises "[Errno 18] Invalid cross-device link" error). Since all we need to do is rename files you can use os.system("mv source destination") which renames files from shell.

Hope this helps ;)

@sartic: nadam se da i tebi hrvatski radi sada kao i meni ;)

---

### Post by sartic on 2010-09-19
thx (hvala :)

last time i boot in merkat there was no sound and upgrade was over 180MB.

---

### Post by vulture on 2010-09-19
I noticed one more bug, currently there is no way to select english for menus and windows and croatian (or any other language for that matter) for numbers, dates and currency amounts. If you somehow manage to do that, computer will set itself to languge for currency, dates etc. at next boot.

---

### Post by sartic on 2010-09-21
i am dissapointed width this version, i will stay on jaunty on laptop and lucid for my desktop/servers.

---

### Post by Yumi on 2010-09-21
This bug hit me to, just a few minutes ago. I tried to be clever and maybe repair another bug by reinstalling libwnck-common and libwnck22 from command line.

It did not solve my other bug, but now language switching does not work anymore. In my chase I try to use German.

Edit: The situation got back to normal after a restart! So seems to have something to do with libwnck.

Michael

---

