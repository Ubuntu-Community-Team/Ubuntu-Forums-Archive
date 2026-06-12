---
title: "New iPod Nano not working in Amarok"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by Nevon on 2007-11-28
From googling, I've found that the new 4gb iPod Nanos (the one with video) doesn't work with the current version of Amarok (1.4.7), due to some new encryption-thingy. However, it seems to be working in version 1.4.8, but it's not in the repositories yet. I don't want to be compiling from source or whatever, so does anyone have an idea of when the repositories will be updated with this fairly important addition? Right now I'm unable to transfer music to my iPod, and it is a little annoying.

---

### Post by Craigus on 2007-11-28
> I don't want to be compiling from source or whatever

It isn't particularly difficult to do, why not give it a try ?

---

### Post by Nevon on 2007-11-29
Simply because I wouldn't know how to, and I've heard that you're not supposed to install stuff via source, you should install it from your package manager.

---

### Post by tgalati4 on 2007-11-29
You are not supposed to install stuff that you don't know where it came from.  Getting the latest source from the Amarok repository seems low risk.  Just follow the instructions in the README.  It's not hard.  Be sure you load the -dev libraries as needed.  They will show up as errors when you try to compile if you don't have them loaded.

Or wait and grumble.

---

### Post by Nevon on 2007-11-29
How long would I have to wait? 6 months or 2 weeks?

---

### Post by Elotero on 2007-11-29
> **Nevon said:**
> From googling, I've found that the new 4gb iPod Nanos (the one with video) doesn't work with the current version of Amarok (1.4.7), due to some new encryption-thingy. However, it seems to be working in version 1.4.8, but it's not in the repositories yet. I don't want to be compiling from source or whatever, so does anyone have an idea of when the repositories will be updated with this fairly important addition? Right now I'm unable to transfer music to my iPod, and it is a little annoying.


Im having trouble with an Ipod Nano thats not as new.. but the same problem. I can see my songs and play them but cant transfer music..  the program that DID work was some program that popped up when i plugged in the ipod ...until i had 2.9 gigs loaded.. it crapped on me when i tried to load more songs and said there was no more room. it was called Music Player.. i think..

---

### Post by Nevon on 2007-11-30
I tried installing from CVN, but I just got this "*** KDE requires automake 2.56 or newer" or something similar to it. I tried "AUTOMAKE=automake-1.6 make -f Makefile.cvs" as it says in the help section, and I also tried "AUTOMAKE=automake-2.56 make -f Makefile.cvs" but neither worked. I have autoconf installed.

EDIT: Hmm, installed automake, and got a bit further. However, I am encountering problems further along. I'm following the guide [here]("http://amarok.kde.org/wiki/Download:SVN"). I get to "./configure --enable-debug=full --prefix=`kde-config --prefix`", but when I try to make, it says there's no makefile to be found.

---

