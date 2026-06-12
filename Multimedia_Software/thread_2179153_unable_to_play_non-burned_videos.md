---
title: "unable to play non-burned videos"
date: 2013-10-06
forum: Multimedia Software
---

### Post by Frank_Callo on 2013-10-06
Hi all

I am running ubuntu 12.4 and am using movie player to play DVDs.  Funny thing, videos that people have burned for me fun fine but when ever I try to lay any "official" printings of DVDs (like my grand daughter's disney movies" I get an error message saying that the problem is probably that I don't have a "decryption library".  I installed a DVD/Blue Ray decrypter from the software center but it didn't solve the problem.

Anyone else have this problem and what, if anything, can I do bout it?

Thanks
Frank

---

### Post by Bashing-om on 2013-10-06
Frank_Callo; Hi !

Many "codecs" to play DVD's are not "freely" open source // and require the installation of additional software to do so.

Let's look and see if these abilities are presently installed:
Terminal code;
```

dpkg -l ubuntu-restricted-extras

```
If that command returns:
> 
sysop@1304mini:~$ dpkg -l ubuntu-restricted-extras
dpkg-query: no packages found matching ubuntu-restricted-extras

Then; You need to install the packages to cope with these required codecs.
terminal code:
```

sudo apt-get install ubuntu-restricted-extras

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

