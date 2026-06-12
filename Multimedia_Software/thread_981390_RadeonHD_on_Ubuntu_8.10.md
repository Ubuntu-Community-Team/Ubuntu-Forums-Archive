---
title: "RadeonHD on Ubuntu 8.10"
date: 2008-11-13
forum: Multimedia Software
---

### Post by another_sam on 2008-11-13
Hi all.

A week ago I followed the steps in [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) but I got this error when I execute sudo ./autogen.sh --prefix=/usr :

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I m4
aclocal: couldn't open directory `m4': No such file or directory
autoreconf: aclocal failed with exit status: 1

What can I do?

Thank you.

p.s.: Yes I did wrote that "autogen.sh does not work for me. output:". I'll erase it quickly if you find it is not a good place.

---

### Post by Yellow Pasque on 2008-11-13
Did you install all of the dependencies as instructed in the first part of the document? what happens when you try to:
```
sudo apt-get install libtool m4
cd /usr/src/xf86-video-radeonhd/
sudo libtoolize
```

EDIT: I am the author of the document, so direct all flames at me. I tried to write it from the perspective of a fresh install (because my system has loads of development libraries installed and has been drastically changed since I installed Gutsy Alpha several moons ago). Apparently, I missed something.

---

### Post by another_sam on 2008-11-13
> **Temüjin said:**
> Did you install all of the dependencies as instructed in the first part of the document?

Yes.

> **Temüjin said:**
> what happens when you try to:
```
sudo apt-get install libtool m4
cd /usr/src/xf86-video-radeonhd/
sudo libtoolize
```

Yeah!! doing libtoolize in that directory solved the problem. thank you very much!

So the fix for the document should be adding before 
```
sudo ./autogen.sh --prefix=/usr
```
this lines:
```
sudo apt-get install libtool m4
sudo libtoolize
```

edit.: I just edited the document. I hope you like it.

---

### Post by Yellow Pasque on 2008-11-14
I'm glad it worked for you. Thank you for helping me test the procedure.

I think I see the problem now. The libtool and m4 packages should have been installed (along with a lot of other packages) by the apt-get build-dep command, but this command only works properly if "Source Code" repos are enabled in System -> Administration -> Software Sources.

I will edit the doc to use specific package names with Intrepid. I also want to add sections on updating the driver and comfirming direct rendering works (with glxinfo).

---

### Post by another_sam on 2008-11-14
> **Temüjin said:**
> I think I see the problem now. The libtool and m4 packages should have been installed (along with a lot of other packages) by the apt-get build-dep command, but this command only works properly if "Source Code" repos are enabled in System -> Administration -> Software Sources.

I yet had "Source Code" repositories enabled. I don't know if this is the default setting, though. I believe to remember that, for my case, "sudo apt-get install libtool m4" did nothing (just confirmed the packages were yet installed). However, I'm 100% sure that "sudo libtoolize" did quite stuff and printed several lines when I executed it; "sudo libtoolize" is what made autogen work.

> **Temüjin said:**
> I will edit the doc to use specific package names with Intrepid. I also want to add sections on updating the driver and comfirming direct rendering works (with glxinfo).

Confirming and updating... [http://icanhascheezburger.files.wordpress.com/2007/07/excellent.jpg](http://icanhascheezburger.files.wordpress.com/2007/07/excellent.jpg)

---

