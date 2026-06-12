---
title: "[SOLVED] src direcotry of linux kernel"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by m.h.shams on 2006-06-22
dear firends.

during installation of a software it need to know linux kernel src directory.
and i can't find this directory.

anyone know that where is linux src directory on ubuntu 6.06 ?


thanks.
shams

---

### Post by jvl on 2006-06-22
the linux-source package puts linux-source-2.6.15.tar.bz2 file into /usr/src

you need to unbzip and untar it with tar xjf linux-source-2.6.15.tar.bz2.

You could as well copy it to arbitrary location and unpack it there.

---

### Post by m.h.shams on 2006-06-22
[QUOTE=jvl]the linux-source package puts linux-source-2.6.15.tar.bz2 file into /usr/src

you need to unbzip and untar it with tar xjf linux-source-2.6.15.tar.bz2.

You could as well copy it to arbitrary location and unpack it there.[/QUOTE]

i can't connect internet with ubuntu, 

is it posible to download it from windows and then copy it to ubuntu ?

---

### Post by jvl on 2006-06-22
Could be possible, the apt servers are ordinary http servers, so I believe you could browse it the usual way. I don't know how to quickly find the package you're looking for though ...

look up the correct url in /etc/apt/sources.list and copy & paste the url starting with http:// to the browser.

---

