---
title: "The Infamous Linksys WPC54G - v3 Wireless Card and Death"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by lsyn on 2006-07-14
Hi all,

In attempting to get my card to work, I followed the wonderful documentation at 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper),

which involved installing a new Broadcom driver from a nfity German site and performing some configuration tasks.  Well, my card is finally capable of scanning properly, so the driver must be doing something right.  My issue is with iwconfig...

According to the (man)ual pages, iwconfig doesn't support passphrases!  ](*,) This is a problem since my local wireless network uses a passphrase.  I don't know a lot about networking, so I don't know how to get around this (if it is possible.)  So, I have two related questions,

1.) Is there a version of iwconfig available that supports passphrases?

2.) If not, is there a way to get around the passphrase?

DJ

---

### Post by bigken on 2006-07-14
Try this it worked for me ;) [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

