---
title: "Restricted Formats"
date: 2011-12-03
forum: Multimedia Software
---

### Post by John Peschken on 2011-12-03
I have been using Ubuntu since 10.04, tried all the versions in between, and decided that I am an LTS sort of guy.  I reinstalled 10.04.03 today.  When I tried to install MP3 support using the method in the Ubuntu  Community documentation, here is what happened.

```
john@ASUS-904:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package ubuntu-restricted-extras**
john@ASUS-904:~$ 

```

Ubuntu could not find the package.  How do I get it where Ubuntu can find it?

---

### Post by An Sanct on 2011-12-03
The 'Multiverse' repositories have to be enabled ...

> The ubuntu-restricted-extras is available in the multiverse repository  (the repsoitory especially for software with copyright/patent issues in  some areas), it is enabled by default for recent versions of Ubuntu  (9.04 or newer).  If you have an older version, you may need to manually  enable it.  The wiki page on [enabling it]("https://help.ubuntu.com/community/Repositories/Ubuntu") or the alternative for [enabling it using the terminal]("https://help.ubuntu.com/community/Repositories/CommandLine").  

---

### Post by John Peschken on 2011-12-03
Apparently, I had done it right before I posted here.  Shortly after I called for help, Ubuntu pulled down a large pile of updates.  After those were applied it worked.  I didn't do a thing except allow the updates.  Something in there must have solved the problem.

---

### Post by John Peschken on 2011-12-03
> **An Sanct said:**
> The 'Multiverse' repositories have to be enabled ...

That's strange.  It was fresh install of 10.04 LTS.  As I understand it, they should have been enabled by default.  Apparently they were not!  The updates fixed it somehow.

---

### Post by CryptAck on 2011-12-03
> **John Peschken said:**
> That's strange.  It was fresh install of 10.04 LTS.  As I understand it, they should have been enabled by default.  Apparently they were not!  The updates fixed it somehow.

I recall a checkbox that you can select on install.

---

### Post by John Peschken on 2011-12-03
> **CryptAck said:**
> I recall a checkbox that you can select on install.


If the install did that I missed it.  My recollection is that the checkbox did not appear until 10.10 or after.  If it appeared on my 10.04, I definitely didn't select it and the problem sorted itself out after some upgrades went it.

---

### Post by An Sanct on 2011-12-05
Well, if you followed the advice on that page, you gave us, it should work...

PS. Please mark this thread as solved, if you are happy with the outcome ;)

---

### Post by John Peschken on 2011-12-05
That was the trouble.  I followed the instructions, as I had done successfully in the past, but it did not work until the Ubuntu updates happened.  

I will look again for the "solved" button but could not find it last time I looked.

---

