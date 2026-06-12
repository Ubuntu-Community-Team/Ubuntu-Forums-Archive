---
title: "VLC Advice Please"
date: 2016-06-30
forum: Multimedia Software
---

### Post by Quarkrad on 2016-06-30
Running 16.04 (dual boot).   I have all the software installed to run dvds/VLC in 16.04.  Burnt a dvd on windows 10 and dvd plays fine via VLC in win10.  In VLC on ubuntu the opening menu plays fine with audio but when you select MOVIE I get a back/blank screen - the same applies if I choose individual chapters.  However, if I choose to open a file and navigate to one of the vob files on the dvd it plays in VLC.  Is this something to do with ripping/burning in win10 or is something missing in the setup of VLS on my ubuntu side?

---

### Post by Autodave on 2016-07-01
Have you installed the restricted extras (assuming that it is legal for you to do so? Assuming you are running Ubuntu, you need the "Ubuntu restricted extras" and "ubuntu restricted add-ons". For xubuntu, the Xubuntu restricted files. Then, make sure that "libdvdread4" is installed.

---

### Post by Quarkrad on 2016-07-02
Both restricted extras and addons are installed and say they are the latest versions.  Also, libdvdread4 is installed.  I can play my troublesome dvd on my domestic dvd player as well as win10.  I have also played two commercial dvds on my 16.04 system and they play - although I would say 16.04 struggles slightly.  On win10 they play without hesitation.

---

### Post by sudodus on 2016-07-02
There might be two problems

- Not good enough drivers or graphics chip to play graphics well.

- Licensing problem

DVD disks and players are fenced in with patents and proprietary issues. It is possible that there is no workaround in your 'restricted extras' or at all in linux for this particular DVD. I have similar problems with some DVDs, while others work well in Ubuntu family operating systems.

- Have you tried other video players, for example mplayer or Parole? They might select slightly differently from the available codecs.

- You can also try to find and install some other library of codecs and other multimedia software.

---

### Post by Quarkrad on 2016-07-02
I would be surprised if ti were a graphics issue as this is not 'commercial film' as such - the graphics, if anything, are more standard type definition rather than hd type graphics.  I have tried m[layer as well - that does not like it.  I installed Parole as suggested and although it would not play I did get an error message - would this suggest the licensing problem?

---

### Post by sudodus on 2016-07-02
You can search for codecs and other multimedia tools via ***synaptic***. I would recommend that you start with what is available via the repositories.

It could be that licensing/encryption is the problem, but let us wait for input from other people, and maybe tips about suitable library packages to install.

---

### Post by mc4man on 2016-07-03
never mind..
edit: I'd try re-burning the dvd in windows with [ImgBurn]("http://www.imgburn.com/index.php?act=download&") if you can.

---

