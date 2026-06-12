---
title: "From where can I find a media codecs with no depedencies...?"
date: 2009-03-05
forum: Multimedia Software
---

### Post by rajeev3001 on 2009-03-05
hi,
I want to install win-32 media codecs to my Ubuntu system. I can't connect to internet using Ubuntu, so 'sudo apt-get' doesn't work. I want to download the codecs from a Windows system and then install them on ubuntu. 

Is there a place find a full .deb package with all dependencies solved?
 
[ So far what I've found were full of unsolved dependencies and I found it really difficult to download all the required .deb packages manually....]

Thanks in advance.

---

### Post by wolfen69 on 2009-03-05
unfortunately, i have never seen packages that have all dependencies resolved.

below are the 2 sites you will need to get required packages.

[Medibuntu]("http://packages.medibuntu.org/")

[Ubuntu]("http://packages.ubuntu.com/")

hopefully, someone else can chime in with a suitable answer.

---

### Post by rajeev3001 on 2009-03-06
Seems like there are no such packages with dependencies resolved. 

Thanks for your reply.

---

### Post by mc4man on 2009-03-06
In this case you only need 2 packages, easy to do.
Go here and download libstdc++5 for your version of ubuntu (page is for intrepid, switch if needed.

[http://packages.ubuntu.com/intrepid/libstdc++5](http://packages.ubuntu.com/intrepid/libstdc++5)

Then go here, pick your ubuntu version and dl w32codecs

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Transfer both to pc, install libstdc++5 first, then w32codecs and your good

---

### Post by binbash on 2009-03-06
go to mplayer site, download codec pack and extract it

---

