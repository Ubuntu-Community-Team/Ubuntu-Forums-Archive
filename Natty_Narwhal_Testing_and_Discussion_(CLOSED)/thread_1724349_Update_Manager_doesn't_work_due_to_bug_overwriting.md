---
title: "Update Manager doesn't work due to bug overwriting one of it's repository list's?"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ShatPank on 2011-04-08
I tagged this onto an old thread a couple of day's ago, but it seems to have gone dead now, so I thought I'd post it in a new thread instead.

Basically, a few day's ago, I ran Update Manager, and whilst it was updating it's repo list's, our internet went down.

Since then, when I try to open update manager I get a window pop up saying:

**[SIZE=2]Could not initialize the package information[/SIZE]**  An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.


If I run sodo apt-get update, I basically get the same error, it's an error with the exact same file anyways...

After poking to the directory it states and finding the file, I opened it so see it had been completely over written with the html code etc that make's up BTHomeHub's "create a connection" page.

Could someone please explain to me how to restor the default file? or just post the contecnt's of their file please?
If it makes any difference, I'm running 64bit

Thanks
Stu

---

### Post by RomeReactor on 2011-04-08
Hi. That happened to me recently. Try this in the terminal:
```
sudo rm /var/lib/apt/lists/*
```
```
sudo apt-get update
```

---

### Post by ShatPank on 2011-04-08
Sorry, I've been out all day, I tried what you said but get a message saying:

:~$ sudo rm /var/lib/apt/lists/*
[sudo] password for stuart: 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory


Being fairly new to linux, I really have no idea what to do when thing's don't do what their expected to do

---

### Post by ShatPank on 2011-04-08
Infact it seems it DID work properly, as after running update, it did fix it... 

Thank you very much, I was getting quite frustrated not being able to update =)

---

