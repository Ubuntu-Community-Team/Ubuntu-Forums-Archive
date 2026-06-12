---
title: "Acroread in Natty?"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-04-05
Anybody knows when Acroread becomes available in Natty or else how to handle pdf files?

Michael

---

### Post by MadCow108 on 2011-04-05
no idea why its not in natty or if it will be added on release, but I for sure do not miss that bloatware.

There are plenty of good free alternatives:
evince, xpdf, okular, xournal, pdftk, ...

---

### Post by IanW on 2011-04-05
"Evince" is the standard pdf reader in Ubuntu.

[https://launchpad.net/ubuntu/natty/+source/evince]("https://launchpad.net/ubuntu/natty/+source/evince")

---

### Post by ronacc on 2011-04-05
you can get acroread from adobe and install it from terminal , Evince (document reader) also does pdf's and should be part of your default install.

---

### Post by gerowen on 2011-04-05
As has been earlier stated, Evince is good.  I highly recommend it.  Opening the same PDF file it takes 1/3 as long to open and display the document when compared to Adobe Reader.

---

### Post by Yumi on 2011-04-05
Thanks for the opinions. I did not realise that I only use acroread for reading PDF's. Settled now as advised for Evince as reader and for PDFedit 
as a Editor. This combination seems to fill my needs.

(Tried to install Evince as I did not realise that it comes under the name of "Documentviewer"!)

Michael

---

### Post by jamiedeith on 2011-04-06
On occasion I do have a use for Adobe Reader, as evince sometimes fails to print properly.  As a workaround I installed using Adobe's install program at [http://get.adobe.com/reader/](http://get.adobe.com/reader/) which seems to do the trick.

---

### Post by cariboo on 2011-04-06
The Maverick version of Acroread is in the partner repository, it should work. You can get it [here]("http://archive.canonical.com/ubuntu/pool/partner/a/acroread/")

---

### Post by Harry33 on 2011-04-06
> **cariboo907 said:**
> The Maverick version of Acroread is in the partner repository, it should work. You can get it [here]("http://archive.canonical.com/ubuntu/pool/partner/a/acroread/")

However, that is only a 32-bit application. So no native 64-bit acroread is available.

---

### Post by ronacc on 2011-04-06
install using ```
dpkg --force-architecture -i <name> 
```

---

### Post by cariboo on 2011-04-06
If you get the 64-bit deb, you don't have to force anything.

---

### Post by Harry33 on 2011-04-06
> **cariboo907 said:**
> If you get the 64-bit deb, you don't have to force anything.

Cariboo907,

I don't think the package acroread_9.4.2-0maverick1_amd64.deb is a native 64-bit one.
It depends on these additional 32-bit packages:
ia32-libs, lib32asound2, lib32bz2-1.0, lib32gcc1, lib32ncurses5, libncursesw5, lib32stdc++6, lib32v4l-0, lib32z1, libc6-i386.

---

### Post by cariboo on 2011-04-06
I know it isn't a true 64-bit package, but you shouldn't have to use the  --force option to install it. I've got the ia32-libs already installed, so all I had to do is use gdebi to install Acroread, it didn't pull in any other packages.

---

