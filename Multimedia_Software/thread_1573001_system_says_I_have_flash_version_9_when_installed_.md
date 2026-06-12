---
title: "system says I have flash version 9 when installed v 10 flash and google flu"
date: 2010-09-12
forum: Multimedia Software
---

### Post by tommynz1975 on 2010-09-12
I people

I am suffering google flu and getting no where fast

I have tried to upgrade flash to its current installation 10.x from 9.x

I have tried 
:~$ sudo apt-get remove flashplugin-nonfree
followed by

$ sudo apt-get install flashplugin-nonfree
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 187155 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.82.76ubuntu0.9.04.1_i386.deb) ...
Setting up flashplugin-nonfree (10.1.82.76ubuntu0.9.04.1) ...


and still it reports I have installed
9,0,999,0

the system is 
uname -a
Linux wheels 2.6.28-19-generic #64-Ubuntu SMP Wed Aug 18 20:55:57 UTC 2010 i686 GNU/Linux


I believe this is 9.04

after screaming what should I do?

I think the quake here in christchurch nz has knocked the last few brain cells loose.

---

### Post by mikewhatever on 2010-09-12
> **tommynz1975 said:**
> .........

and still it reports I have installed
9,0,999,0
.....


Forgive me for possibly an obvious question, but who's it?
Have you restarted Firefox?

---

### Post by tommynz1975 on 2010-09-12
yes I have even rebooted the system

---

### Post by kerry_s on 2010-09-12
> sudo apt-get remove flashplugin-nonfree

that does not fully remove, you need to purge, use synaptic thats what it's there for, you can see what your doing.

---

### Post by lovinglinux on 2010-09-12
The problem is that you also has gnash plugin installed, which is the one being detected by Firefox. Remove gnash with:

```
sudo apt-get purge mozilla-plugin-gnash
```

or get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by tommynz1975 on 2010-09-13
[QUOTE=lovinglinux;9838963]The problem is that you also has gnash plugin installed, which is the one being detected by Firefox. Remove gnash with:

```
sudo apt-get purge mozilla-plugin-gnash
```

this was not installed so couldn't remove

Synaptic reports the following installed

swfdec-mozilla 0.8.2
libswfdec 0.8.0
flashplugin-installer 10.1.82.7ubuntu0

I will then reboot the system

and open the flash aid link to see if more is in hiding.


Much thanks for all the support.

---

### Post by tommynz1975 on 2010-09-13
okay on reboot 



[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
showed no flash installed,

I clicked the flash aid link, that is shown above  this installed the Firefox plug-in.

The plug-in went to the trouble of telling me what it was going to do
including showing me the exact script that it would execute to remove the out dated rubbish.

The plug in  then installed the current version of 
10.1.82.76

I would encourage people to bookmark this for future reference.

---

### Post by lovinglinux on 2010-09-13
> **tommynz1975 said:**
> okay on reboot 

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
showed no flash installed,

I clicked the flash aid link, that is shown above  this installed the Firefox plug-in.

The plug-in went to the trouble of telling me what it was going to do
including showing me the exact script that it would execute to remove the out dated rubbish.

The plug in  then installed the current version of 
10.1.82.76

I would encourage people to bookmark this for future reference.

I'm glad it worked for you. For the record, FLASH-AID is an extension, not a plugin, although It is basically a flash plugin remover/installer.

---

