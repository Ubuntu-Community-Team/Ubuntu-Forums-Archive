---
title: "Jaunty flash problems"
date: 2009-07-26
forum: Multimedia Software
---

### Post by BaineVII on 2009-07-26
So I just upgraded to Jaunty a day or two ago, and finally decided to try and work on the flash issue. I've read that if you use adobe-flashplugin instead of flashplugin-nonfree it works a lot better...so I uninstalled the latter...I uncommented the partner depositories, so from what I understand that isn't the problem, but when I try to install the adobe plugin:

```
:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate
chris@chris-laptop:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

```

Does anybody know how to fix this?

---

### Post by martinbaselier on 2009-07-26
Go to software sources, in system/settings and turn on multiverse.

---

### Post by BaineVII on 2009-07-26
I went in to find that it was already enabled, however upon exiting it updated -something- and now I'm able to install the adobe plugin.

I still have an issue, though...in the terminal during installation:

> adobe-flashplugin 10.0.2...

But in the plugins section of firefox it still lists flash version 9.x, and it still doesn't work very well...

---

### Post by Soulcage on 2009-07-26
Try dling the deb file from: [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

---

### Post by martinbaselier on 2009-07-26
Ubuntu downloads the file from adobe and doing it this ways makes sure you get updates automatically. 

What's the output of these commands?
**dpkg -l | grep flash**

**locate adobe-flash**

---

### Post by BaineVII on 2009-07-26
```
dpkg -l | grep flash
ii  adobe-flashplugin                          10.0.22.87-2jaunty1                       Adobe Flash Player plugin version 10
ii  flashplugin-installer                      10.0.22.87ubuntu2                         Adobe Flash Player plugin installer

```

```
locate adobe-flash
/usr/lib/adobe-flashplugin
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/share/doc/adobe-flashplugin
/usr/share/doc/adobe-flashplugin/changelog.Debian.gz
/usr/share/doc/adobe-flashplugin/copyright
/var/lib/dpkg/info/adobe-flashplugin.list
/var/lib/dpkg/info/adobe-flashplugin.md5sums
/var/lib/dpkg/info/adobe-flashplugin.postinst
/var/lib/dpkg/info/adobe-flashplugin.prerm
```

According to this I do have the right thing, but firefox says that I still have 9.0...

Methinks some if not all of these files need to be moved to the firefox plugin folder?

---

### Post by martinbaselier on 2009-07-26
None of them need to be moved there. Works fine here without that. Maybe firefox is wrong. 

You could start firefox like this:
firefox -Profilemanager

And then create a new profile.

---

