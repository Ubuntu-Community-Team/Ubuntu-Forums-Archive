---
title: "Natty - Kubuntu - Can't install Firefox"
date: 2011-02-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by TBABill on 2011-02-17
Error I encounter is: > bill@bill-laptop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  latex-xft-fonts
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/16.7 MB of archives.
After this operation, 40.4 MB of additional disk space will be used.
(Reading database ... 117484 files and directories currently installed.)
Unpacking firefox (from .../firefox_4.0~b11+build3+nobinonly-0ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_4.0~b11+build3+nobinonly-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 11.04ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_4.0~b11+build3+nobinonly-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thoughts? I am running 64 bit alpha 2 Natty Kubuntu with updates applied. Chromium installed fine, updates went ok, but I must be missing something for the Firefox install. lib32 files are installed as well for 32 bit apps.

---

### Post by Gavin77 on 2011-02-18
I got around that by first uninstalling kubuntu-firefox-installer and then installing Firefox.

---

### Post by TBABill on 2011-02-18
I actually chuckled when I first read that, but it makes sense. I'll give it a shot when I get home. Never thought it would be as simple as a bad installer. Thanks!!

---

### Post by xebian on 2011-02-18
IMHO it's a case of bad packaging/naming.  firefox.desktop rightfully belongs to firefox but not in kubuntu-firefox-installer.:)

---

### Post by chrisccoulson on 2011-02-18
I've already committed a fix to Firefox for this, but I'm not planning another upload until we get beta 12

---

