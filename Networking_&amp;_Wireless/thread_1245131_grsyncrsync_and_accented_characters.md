---
title: "grsync/rsync and accented characters"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by alenis on 2009-08-20
I am trying to use rsync to sync my home and office PCs over an ssh connection. The office server runs Hardy, at home I use Jaunty. Both PCs use rsync v. 3.0.x
The problem is that filenames containing special characters (e.g. à, ò, è, which unfortunately are very common in Italian and other languages) are not matched correctly. For example, a file name such as
```
Registro Attività
```
looks correct in directory listings in both PCs, and it is correct even if I mount the remote directory on the home computer without specifying any character encoding option; but when I run rsync on the home computer to transfer files from office, the file name in the office PC is reported as
```
Registro Attivit&#9500;á
```
and is considered different from the version I already have on the home computer.
I used this command:
```
rsync -r -n -t -p -o -g -x -v --progress --delete -e ssh alenis@ufficio:/home/alenis/Documenti/ufficio/ /home/alenis/Documenti/ufficio
```
I am aware that rsync includes an --iconv option, that should be used to convert filenames between different character set, but the characters sets in the two computer are the same. This is the output of the locale command:
```

**Home:**
LANG=it_IT.UTF-8
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=

```

```

**Office:**
LANG=it_IT.UTF-8
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=

```

Any help to solve this problem would be greatly appreciated.

---

### Post by pedricus on 2011-05-18
Where you (or anyone else?) ever able to solve this?

I'm still having this problem on 10.10, and I haven't been able to find any answers.

---

