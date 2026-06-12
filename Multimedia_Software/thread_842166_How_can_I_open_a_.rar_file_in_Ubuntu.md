---
title: "How can I open a .rar file in Ubuntu?"
date: 2008-06-27
forum: Multimedia Software
---

### Post by awjm on 2008-06-27
Archive manager doesn't support it, so can I download an add-on or different file manager? And how?

---

### Post by jeroen.kurvers on 2008-06-27
Installing unrar or unrar-free should do the trick.

---

### Post by MonGol on 2008-06-27
for rar-archives there are packages named "unrar" and "rar" (both multiverse). although both are command-line programmes they can be used very easyly:
```
unrar e <archive.rar>
```
or
```
unrar e -p <password> <archive.rar>
```
(if the archive is protected by a password) unpack archives.

---

### Post by y4h0ooo0 on 2008-06-27
**RAR 3.80 beta 2 for Linux**

[http://www.rarlab.com/rar/rarlinux-3.8.b2.tar.gz]("http://www.rarlab.com/rar/rarlinux-3.8.b2.tar.gz")

---

### Post by bikeboy on 2008-06-27
Just to add some more detail. Plain 'unrar' has a non-free license (same as on Windows) that stipulates you should trial it for 30 days then pay for it - though that's optional. That version of unrar integrates with Ubuntu's default archive manager program by default, so that's a little easier.

If you don't mind the command line, unrar-free will work for all except a limited number of the most recent .rar files.

---

### Post by Major_Kong on 2008-06-27
Just : sudo apt-get install unrar (or look for the package in synaptic)

The archive manager will be able to open .rar after that.

---

### Post by Trollslayer on 2008-06-27
Search for 'rar' in Synaptic.

---

### Post by kriukov on 2008-06-27
7-zip has always unpacked *.rar files for me (and many more, even *.chm):

sudo apt-get install p7z-full
7z x *.rar

---

