---
title: "[SOLVED] Printing in Mythbuntu?"
date: 2007-11-15
forum: Mythbuntu
---

### Post by pssturges on 2007-11-15
Hi,

I've set up my gutsy mythbuntu frontend/backend machine using the Mythbuntu live cd. I would like to also use this machine as a print server on my home network. Problem is, there doesn't seem to be any printing funtionallity in Myhthbuntu. I assume I wiil need to install some packages with synaptic, just not sure which ones(Cups?).

I've set up printer sharing with Ubuntu before, so I'm ok with all the configuration, I just need to know how to get the printing functionallity installed.

Thanks
Phil

---

### Post by pssturges on 2007-11-17
Bump!

---

### Post by macegr on 2007-11-18
Mythbuntu is a standard Xubuntu installation with MythTV preinstalled. The process should be identical to that used for any other Ubuntu machine. For example:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29")

I don't use Live CDs so I don't know if that will be a major roadblock. Without persistent storage of the CUPS application you might have to reinstall it every time MythTV hard-locks your system.

---

### Post by superm1 on 2007-11-18
> **macegr said:**
> Mythbuntu is a standard Xubuntu installation with MythTV preinstalled. The process should be identical to that used for any other Ubuntu machine. For example:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Print_Server_.28cupsd.29)

I don't use Live CDs so I don't know if that will be a major roadblock. Without persistent storage of the CUPS application you might have to reinstall it every time MythTV hard-locks your system.
I wouldn't entirely agree with this.  A standard Xubuntu install includes a lot more then mythbuntu does.  Here is the cups related items that come with Xubuntu:

```
supermario@kingkoopa:~$ apt-cache depends xubuntu-desktop | grep cup
  Depends: cupsys
  Depends: cupsys-bsd
  Depends: cupsys-client
  Depends: cupsys-driver-gutenprint
  Recommends: cups-pdf
  Recommends: hal-cups-utils

supermario@kingkoopa:~$ apt-cache depends xubuntu-desktop | grep print
  Depends: cupsys-driver-gutenprint
  Depends: openprinting-ppds
  Recommends: gimp-print
  Recommends: system-config-printer
  Recommends: xfprint4


supermario@kingkoopa:~$ apt-cache depends xubuntu-desktop | grep print
  Depends: cupsys-driver-gutenprint
  Depends: openprinting-ppds
  Recommends: gimp-print
  Recommends: system-config-printer
  Recommends: xfprint4
```

Install each of those listed items in the depends and recommends and you should be good to go.

---

### Post by pssturges on 2007-11-18
Yep, that did it. Thanks for your help guys, much appreciated.

Phil

---

### Post by tony.morse on 2009-08-08
Wicked, same problem fixed thanks to this post.  Cheers

---

### Post by sawbuck on 2009-10-09
Excellent!  I've been trying to find a printing solution for weeks.  I used the Synaptic Package Manager - with a little stumbling - to install the depend/recommend pacjkages and got a printer finally!  Some packages were named differently, though.  I have an Epson Stylus Photo R320 attacthed to an XP box. Test page printied fine.  Thanks.....

---

