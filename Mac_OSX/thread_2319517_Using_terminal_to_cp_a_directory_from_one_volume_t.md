---
title: "Using terminal to cp a directory from one volume to another with error log."
date: 2016-04-05
forum: Mac OSX
---

### Post by jrl155la on 2016-04-05
A friend of mine said that I could use this pice of code to copy files from one location to another and have it also output an error log
```
SOURCEDIR="/Volumes/FreeAgent GoFlex Drive/Anime"
DESTDIR="/Volumes/5TB FreeAgent GoFlex Drive/Anime"
for d in "${SOURCEDIR}/"*; do echo 'copying `basename "${d}"`';cp -r "${d}" "${DESTDIR}/`basename ${d}`" 2> err.log; done
```but when I use this code in a .sh file it does the following to the first copied dir, [ATTACH=CONFIG]268187[/ATTACH] it creates the first folder and gives it the label of the drive and the name of the first folder combined.
The original line of code he gave me, that I was going to used before I asked if he could have it output the errors to a log, was```
SOURCEDIR="/Volumes/FreeAgent GoFlex Drive/Anime"
DESTDIR="/Volumes/5TB FreeAgent GoFlex Drive/Anime"
for d in "${SOURCEDIR}/"*; do echo "copying `basename "${d}"`"; cp -r "${d}" "${DESTDIR}"; done
```and it worked fine, but now how do I get the error logging pice of code to work?

---

### Post by coffeecat on 2016-04-05
Your screenshot shows what appears to be a MacOS Finder window. What operating system are you using?

**Edit**: The references to AirDrop and iCloud Drive suggest that you are running MacOSX Yosemite, rather than a Linux desktop themed to look like MacOS, so I've moved this thread to the Other Operating Systems -> Mac OSX sub-forum.

You posted this bash-related question in New to Ubuntu, the tagline for which clearly states:

> The perfect place to post for your Ubuntu support if you are new to Linux.


Although members proficient in bash in Ubuntu may be able to help you, you may be better off in a MacOS forum which caters for those Mac users who wish to use the terminal.

---

### Post by CharlesA on 2016-04-05
In addition to what Coffeecat said, I have a couple questions:

Why are you using cp rather than rsync? Is there a specific reason you want to get a list of errors that occurred during the copy?

Try this:

```

#/bin/bash

source="/Volumes/FreeAgent GoFlex Drive/Anime"
destination="/Volumes/5TB FreeAgent GoFlex Drive/Anime"
error="/home/$(whoami)/error.log"
cp -rv $source $destination 2> $error
```

---

