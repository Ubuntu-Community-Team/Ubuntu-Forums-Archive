---
title: "Synaptic package manager not finding new verison for mkvtoolnix using apt line"
date: 2014-04-18
forum: Multimedia Software
---

### Post by Wizard2829 on 2014-04-18
Hi i use mkvtoolnix on ubuntu and i noticed ubuntu 14.04 comes with mkvtoolnix 6.7.0 I am having issues getting 14.04 to find newest verison of mkvtoolnix with the deb apt line I have. For some reason synaptic package manger is not finding it a upgrade of mkvtoolnix with the apt line added and the persons key. I cannot even find one listened under force verison. Any help would be great. Its bugging me causes i never ran into this issue before with any ubuntu verisons.

---

### Post by Bashing-om on 2014-04-18
Wizard2829; Hi !

I no longer use synaptic - a front end for apt, and I do not have it installed, so can not address your question directly.
However, a direct application of apt, what returns from terminal command:
```

apt-cache policy mkvtoolnix

```

Maybe 'mkvtoolni' has not made it yet to 14.04's repository ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ron998 on 2014-04-18
> **Wizard2829 said:**
> Hi i use mkvtoolnix on ubuntu and i noticed ubuntu 14.04 comes with mkvtoolnix 6.7.0 I am having issues getting 14.04 to find newest verison of mkvtoolnix...
Hi
Instructions are here ---> [http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu)


```
@Xubuntu:~$ cat /etc/issue
Ubuntu 14.04 LTS \n \l
```

```
@Xubuntu:~$ mkvmerge
mkvmerge v6.9.1 ('Blue Panther') 32bit built on Apr 18 2014 18:26:24
```

---

### Post by Wizard2829 on 2014-04-18
Its been fixed on its own the owner of mkvtoolnix released a newer verison from 6.9.0  to 6.9.1 and this time synaptic picked it up and let me upgrade to the newer verison. correction im now getting this error E: /var/cache/apt/archives/mkvtoolnix-gui_6.9.1-0~bunkus01_i386.deb: trying to overwrite '/usr/share/icons/hicolor/16x16/apps/mkvextract.png', which is also in package mkvtoolnix 6.7.0-1 any idea how to fix this?

---

### Post by ron998 on 2014-04-18
> **Wizard2829 said:**
> ... any idea how to fix this?


Try
sudo apt-get remove mkvtoolnix-gui
sudo apt-get remove mkvtoolnix
sudo apt-get purge mkvtoolnix-gui
sudo apt-get purge mkvtoolnix

Then follow instructions in previous post.

---

### Post by Wizard2829 on 2014-04-18
Thankyou ron998 those steps helped and worked. After i did the steps you gave me i tried to install mkvtoolnix and it installed without any errors this time. Thanks again for your help. Ill keep those steps in mind just in case it happens again to mkvtoolnix or any program.

---

### Post by andrew.46 on 2014-06-26
Mosu never stops:

```

andrew@ilium~$ **[COLOR="#FF0000"]mkvmerge --version[/COLOR]**
mkvmerge v7.0.0 ('Where We Going') 64bit built on Jun 27 2014 12:18:03

```

---

