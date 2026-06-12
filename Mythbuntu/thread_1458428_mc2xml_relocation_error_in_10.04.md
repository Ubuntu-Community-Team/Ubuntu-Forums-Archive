---
title: "mc2xml relocation error in 10.04"
date: 2010-04-20
forum: Mythbuntu
---

### Post by Lepy on 2010-04-20
With the upgrade to 10.04, I decided to utilize my HVR-1600's s-video input to record from a neglected STB since it allows access to a few extra channels the analog tuner will not pick up, and on a majority of channels, the analog tuner signal has recently regressed back to this: [http://i37.tinypic.com/14kbog2.jpg](http://i37.tinypic.com/14kbog2.jpg)

After editing the analog mc2xml.chl, I tried running a custom script to update to my listings. I get this error:

```
:~$ ./mc2xml/update.sh 
Loading ..... : mc2xml (c) <mc2xml@gmail.com> (2009-04-20)
Reminder .... : Unauthorized redistribution prohibited.
Reminder .... : If this software is useful, please donate!
Reading ..... : ./analog/mc2xml.dat
mc2xml: relocation error: /lib32/libresolv.so.2: symbol strlen, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
Loading ..... : mc2xml (c) <mc2xml@gmail.com> (2009-04-20)
Reminder .... : Unauthorized redistribution prohibited.
Reminder .... : If this software is useful, please donate!
Reading ..... : ./digital/mc2xml.dat
mc2xml: relocation error: /lib32/libresolv.so.2: symbol strlen, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```

I ran getlibs against mc2xml just in case, but it says all deps are satisfied. Any ideas?

---

### Post by Lepy on 2010-04-20
Spoke too soon! I have had a set-it-and-forget-it mentality with my mc2xml listings since they have just worked. Haven't refreshed the program in over a year.

I downloaded mc2xml from the author's site, replaced the (older?) referenced versions with the newly downloaded version, re-ran the script, and the guide updated as usual.

I guess mc2xml has been updated, but I could find no change log or anything on the website. The output of the program has definitely changed.

> :~/mc2xml$ ./update.sh 
Loading ..... : mc2xml (c) <mc2xml@gmail.com> (v1.0)

---

### Post by superm1 on 2010-04-20
> **Lepy said:**
> Spoke too soon! I have had a set-it-and-forget-it mentality with my mc2xml listings since they have just worked. Haven't refreshed the program in over a year.

I downloaded mc2xml from the author's site, replaced the (older?) referenced versions with the newly downloaded version, re-ran the script, and the guide updated as usual.

I guess mc2xml has been updated, but I could find no change log or anything on the website. The output of the program has definitely changed.
As indicated previously, mc2xml may be illegal and discussion of it is not allowed on these forums.  Please don't open another thread on it.  I'm going to close this one.

[http://ubuntuforums.org/showpost.php?p=6181143&postcount=16](http://ubuntuforums.org/showpost.php?p=6181143&postcount=16)

---

