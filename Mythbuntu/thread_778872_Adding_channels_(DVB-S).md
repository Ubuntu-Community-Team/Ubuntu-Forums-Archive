---
title: "Adding channels (DVB-S)"
date: 2008-05-02
forum: Mythbuntu
---

### Post by the[V]oid on 2008-05-02
Hi, I got the following problem: My MythTV cannot find some encrypted channels I want to watch, although it finds some other encrypted channels of the same provider. I googled a lot and got the impression that it is not possible to add these channels to MythTV: Writing the channels to a channels.conf and importing this one doesn't work as well, MythTV seems just to scan the appropriate transponders and (of course) fails to find them:
```
P 01:11720:hC34:S19.2E:27500:511:512:511:222
P 02:11720:hC34:S19.2E:27500:767:768:767:220
P 03:11720:hC34:S19.2E:27500:2559:2560:2559:242
P 04:11720:hC34:S19.2E:27500:2815:2816:2815:243
P 05:11720:hC34:S19.2E:27500:3071:3072:3071:244
P 06:11758:hC34:S19.2E:27500:2047:2048:2047:221
P 07:11758:hC34:S19.2E:27500:3327:3328:3327:226
P 08:11758:hC34:S19.2E:27500:3583:3584:3583:227
P 09:11798:hC34:S19.2E:27500:3071:3072:3071:224
P 10:11798:hC34:S19.2E:27500:3327:3328:3327:225
P 11:12032:hC34:S19.2E:27500:3071:3072:3071:208
P 12:12032:hC34:S19.2E:27500:3327:3328:3327:209
P 13:12070:hC34:S19.2E:27500:511:512:511:212
P 14:12070:hC34:S19.2E:27500:3327:3328:3327:780
```
I would like to know whether there is another possibility to add these channels before I start hacking the database. Thanks!

---

### Post by p$y on 2008-05-02
Hi,

see the link in my last post:
[http://ubuntuforums.org/showthread.php?t=734796](http://ubuntuforums.org/showthread.php?t=734796)

I've got it to work with phpmyadmin and editing the database.

---

