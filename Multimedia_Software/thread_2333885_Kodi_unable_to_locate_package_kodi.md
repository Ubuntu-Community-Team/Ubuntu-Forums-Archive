---
title: "Kodi unable to locate package kodi"
date: 2016-08-14
forum: Multimedia Software
---

### Post by juancabarrocas on 2016-08-14
I am trying to install KODI on a Rikomagic MK80 Octacore running on Ubuntu 14.04 and everything runs fine until "sudo apt-get install kodi" when I get answer "unable to locate package kodi".

I have only low experience with linux (Ubuntu) and would ask if anybody can give me a help. I chosed a Linus based system for my HTPC because I want to read my media HD which are under HFS (Mac) format.

---

### Post by PaulW2U on 2016-08-14
> **juancabarrocas said:**
> I am trying to install KODI on a Rikomagic MK80 Octacore running on Ubuntu 14.04 and everything runs fine until "sudo apt-get install kodi" when I get answer "unable to locate package kodi".
I understand that kodi is only included in the repositories for later Ubuntu versions. It's certainly included in 16.04.

Take a look at [HOW-TO:Install Kodi for Linux]("http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux") - it looks like you'll have to use a PPA for your version of Ubuntu, i.e. 14.04. When you come to upgrade Ubuntu, whenever in the future that might be, you should stop using the PPA and use the Ubuntu provided version. Hope that helps.

---

### Post by QIII on 2016-08-14
Hello!

I don't know if it became Kodi before or after 14.04.  It might still have been XBMC for 14.04.  Did you try installing XBMC?  

Are you running a Canonical release of Ubuntu or someone else's ARM port?

---

### Post by ajgreeny on 2016-08-14
Yes, it's still xbmc in 14.04 repos.

---

### Post by juancabarrocas on 2016-08-14
Thanks a lot. I'll try xbmc

---

### Post by howefield on 2016-08-14
> **juancabarrocas said:**
> Thanks a lot. I'll try xbmc

That should work but might give you an "old" version, I'd suggest following the advice from PaulW2U :)

---

### Post by juancabarrocas on 2016-08-14
I am runing Linaro Ubuntu on a Rikomagic MK80 Octacore Allwinner

---

### Post by juancabarrocas on 2016-08-14
Thanks. I am trying and shall tell you success or not

---

### Post by hollywoodpete on 2016-08-17
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi

---

