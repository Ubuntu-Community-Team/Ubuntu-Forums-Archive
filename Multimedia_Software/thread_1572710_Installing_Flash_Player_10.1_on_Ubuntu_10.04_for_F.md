---
title: "Installing Flash Player 10.1 on Ubuntu 10.04 for Firefox 3.6.9"
date: 2010-09-11
forum: Multimedia Software
---

### Post by 9dor on 2010-09-11
Hello,

I tried to install Flash Player 10.1 but it didn't work. I noticed that this issue is problematic.
I tried many techniques to install that flash player, all of them didn't work. Among them are:

[LIST=1]
[*]The usual way, by choosing apt [here]("http://get.adobe.com/flashplayer/") and received the usual error message "Package 'adobe-flashplugin' is virtual."
[*][http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
[*][http://www.wetware.co.nz/blog/2010/06/package-adobe-flashplugin-is-virtual-when-installing-flash-on-firefox-or-chrome-ubuntu-lucid-lynx-10-04-64/](http://www.wetware.co.nz/blog/2010/06/package-adobe-flashplugin-is-virtual-when-installing-flash-on-firefox-or-chrome-ubuntu-lucid-lynx-10-04-64/)
[*]etc, whatever was found on the internet
[/LIST]
Info:

```
$ uname -a
Linux rep-desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
$ cat /etc/issue
Ubuntu 10.04.1 LTS \n \l
```
[LIST]
[*]Firefox v3.6.9
[*]This is a **64 bit** system
[/LIST]
I appreciate the time you're taking to read this post.

---

### Post by Yellow Pasque on 2010-09-11
Try again (and read the instructions carefully this time): [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

---

### Post by 9dor on 2010-09-12
> **Temüjin said:**
> Try again (and read the instructions carefully this time): [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)
Hi,

I did that again, but to no avail.

When I go to: [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
It says:
> You have version 9,0,999,0 installed
Which is a really old version, so I disable it because of security reasons.

---

### Post by andymorton on 2010-09-12
It would be easier to install the ubuntu restricted extras package from the software centre. This includes Flash and various other useful things, e.g. Java, MPEG support and other fonts. 

andy

---

### Post by 9dor on 2010-09-12
> **andymorton said:**
> It would be easier to install the ubuntu restricted extras package from the software centre. This includes Flash and various other useful things, e.g. Java, MPEG support and other fonts. 

andy
I already have those :\
but thx anyway :)
Maybe should I re-install that package? **Edit: **I tried re-installing, it doesn't work.

---

