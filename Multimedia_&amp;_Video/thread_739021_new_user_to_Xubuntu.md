---
title: "new user to Xubuntu"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by Gavinholmes on 2008-03-29
Hi everyone, im very impressed with this software, but still having afew small teething problems. The main one is for music and playing restricted medias 'Ubuntu restricted extras'. when i go to install this it keeps on coming up with this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Im a complete novice :confused: to this, so  how do you manually install a programme ,if you repley please make it simple for me. the system i have is a Acer apsire 1353 VX  and im running Xubuntu Linux 7.10 i386

Cheer Gav

---

### Post by Ditriker on 2008-03-29
I'll take it you manually want to install programs?. Music at that, I suggest XMMS.

To do this, first go to the terminal.
Type

sudo su

Sudo (do as super user) su (super user) 

It'll ask for your root password. Type it in. It is sometimes your LOG-IN password.

Then, type

apt-get install

and after install make a space and type in the program you want/need which I suggest be xmms.

Thus you type

apt-get install xmms

Press ENTER

It should install, and after that go to applications-soundandvideo and you should see xmms. Otherwise go to the terminal, type in xmms and it should appear. Xmms can play mp3 and ogg vorbis files.

---

