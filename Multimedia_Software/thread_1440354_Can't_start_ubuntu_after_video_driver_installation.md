---
title: "Can't start ubuntu after video driver installation"
date: 2010-03-27
forum: Multimedia Software
---

### Post by steli89 on 2010-03-27
I'm quite new to ubuntu (been using it for 4 months) and i couldn't enable any of the desktop effects. 
So i searched available drivers and found one for my graphics card.
After installing it and rebooting, the system doesn't start, i tried ctrl+alt+f1 for entering in console mode but that doesn't work either.
Has anyone has problems like this before?

---

### Post by coolcaseley67 on 2010-03-27
Hi

-what is your graphics card model eg ?

Thanks

---

### Post by steli89 on 2010-03-27
Ati mobility radeon HD 3650

---

### Post by coolcaseley67 on 2010-03-27
Hi
 
- how did you install it ???
- see [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  and [http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)   for bit and bobs on ATI Drives . 
 
thanks

---

### Post by steli89 on 2010-03-27
Something like System->Administration->Hardware and it detected available drivers to install.

---

### Post by coolcaseley67 on 2010-03-27
hi 
 
- go in to recary mode at the start choose drop root to shell (log-in in needed) now type :```
 fglrxinfo  
```  this will tell you what driver is in use . 
 
hope it helps as in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by steli89 on 2010-03-27
As i said, i'm new to Linux, so can u please tell me how to go into that mode u said there... :)

edit: after choosing linux in grub, a black screen appears

---

### Post by coolcaseley67 on 2010-03-27
Hi 
 
1) turn on your pc .
 
2) a menu will apper give you the choose of 
ubuntu Kenel no ... ( the one you use every day )
_ubuntu Kenel no...  (recovey mode )_ 
windows eg
 
3) choose the unlined one in 2 
 
4) once ubuntu has started up a blue menu will apper , choose drop root to shell (log-in if needed ) 
 
hope it helps

---

### Post by steli89 on 2010-03-27
thank you :)

---

### Post by coolcaseley67 on 2010-03-27
Hi  

anything else just post ! :KS
updated :
mark this as solved it thread tools

---

