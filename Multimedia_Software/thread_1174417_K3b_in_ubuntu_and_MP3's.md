---
title: "K3b in ubuntu and MP3's"
date: 2009-05-30
forum: Multimedia Software
---

### Post by luke0927 on 2009-05-30
OK so i was looking for a new cd burning software brassero freezes up and i have some issues with it sometimes...I saw K3b so it will work fine being a KDE application in GNOME (i installed it any way and it loads up fine) but when i try to add and mp3 player it doesn't like it is there a codec or something to get it to support mp3s in ubuntu?

---

### Post by paxmark1 on 2009-05-30
There are lots of media players for ubuntu. all the way from command line programs such as mpg321 and cplay to ubuntus defarult rhythmbox and the kde application amarok.  

If k3b successfully burns your mp3 to cd4 disks or dvd disks, it is probably working.  If your media player doesn not play mp3, that would be a seperate issue.

What are you using for a media player?

to see if you have the tools to encode mp3s
try

aptitude search lame

aptitude search sox

(not necessary, but k3b likes sox)

If they are not present. install via your  favourite package manager.   



If lame will not install then

sudo aptitude install ubuntu-restricted-extras        or      sudo apt-get install ubuntu-restricted-extras


peace, mark

---

### Post by luke0927 on 2009-05-31
> **paxmark1 said:**
> There are lots of media players for ubuntu. all the way from command line programs such as mpg321 and cplay to ubuntus defarult rhythmbox and the kde application amarok.  

If k3b successfully burns your mp3 to cd4 disks or dvd disks, it is probably working.  If your media player doesn not play mp3, that would be a seperate issue.

What are you using for a media player?

to see if you have the tools to encode mp3s
try

aptitude search lame

aptitude search sox

(not necessary, but k3b likes sox)

If they are not present. install via your  favourite package manager.   



If lame will not install then

sudo aptitude install ubuntu-restricted-extras        or      sudo apt-get install ubuntu-restricted-extras


peace, mark

No i have no problems playing MP3's out of my library just looking for somethign besides brasero to burn them to CD...I downloaded k3b but it like its missing something to let me burn the mp3s to CD.

---

### Post by xc3RnbFO8P on 2009-05-31
Did you install
**libk3b3-extracodecs**
in Synaptic Package Manager

---

### Post by luke0927 on 2009-05-31
Yes that one is installed but not the libk3b2-exrtacodecs

---

### Post by luke0927 on 2009-06-01
bump any idea's or another good burnning program to use.

---

### Post by riggity_ryan on 2009-09-08
Are you sure you have libk3b2-exrtacodecs installed?  I had the same issue as you and installed libk3b2-exrtacodecs (and k3b-i18n, but I doubt that has anything to do with this issue) and can k3b accepts mp3s.

---

### Post by Groszman on 2009-11-13
> **Ringi said:**
> Did you install
**libk3b3-exrtacodecs**
in Synaptic Package Manager

I've got the same problem and I tried to find that package but synaptic says: the is nothing like that in the software sources. using karmic koala.

---

### Post by xc3RnbFO8P on 2009-11-13
In Karmic Koala it is **libk3b6-extracodec**

---

