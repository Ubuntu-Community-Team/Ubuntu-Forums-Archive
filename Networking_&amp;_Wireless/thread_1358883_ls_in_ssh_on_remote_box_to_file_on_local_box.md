---
title: "ls in ssh on remote box to file on local box"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by xboxbman on 2009-12-18
I have an xbox360 with debian running on it, and have no keyboard or mouse connected.  I would like to ssh into the xbox, type ls to list the files, and pipe the output of ls to a file on my laptop.  Is there a simple way to do this?

---

### Post by SoftwareExplorer on 2009-12-18
Assuming ssh is working on the xbox, try this ```
ssh username@xbox "ls /the/directory/you/want/to/see" > file.txt
```
It should put the file in the directory you are currently on in the local computer.

---

