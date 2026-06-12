---
title: "Avidemux slower on Feisty?"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by yanewby on 2007-04-20
I upgraded to Feisty yesterday but the upgrade appears to have slowed Avidemux to a slow crawl.

Prior to upgrading converting a 1 hour AVI would take approximately 1 hour.

After upgrading, doing the exact same conversion is now taking in excess of 3 hours.

Do you have any idea what has caused the decrease in speed?

Let me know if you need any details of my system (all I have done is upgrade from Edgy Eft to Feisty Fawn).

---

### Post by dinoj on 2007-04-21
I have same issue with i386 feisty version and fresh install. I have check  64-bit version of Feisty and avidemux everything is perfect.

---

### Post by yanewby on 2007-04-21
I am using a i386 Feisty upgraded from Edgy.

I have tried a few things but have yet to come up with a solution... I have tried re-installing everything I thought could be related including Avidemux, xvid and other codecs.  I have even tried compiling xvid from source (ensuring ASM was enabled) but this did not help either.

---

### Post by dinoj on 2007-04-21
I thing that problem is with xvid library. I fix it when I grab libxvidcore4_1.1.2-0.1_i386.deb package from debian-multimedia.org

---

### Post by yanewby on 2007-04-21
I have now managed to solve this problem with the help of mean from the Avidemux forums.  The solution was to re-compile the xvid codec with ASM optimization.

This is what you need to do:

1) In Synaptic Package Manager, install yasm and nasm.

2) Download the latest source code from [http://xvid.org](http://xvid.org) and unzip it.

3) In Terminal (subsitute [path to xvid folder] with where you unzipped the xvid source) type:

cd [path to xvid folder]/build/generic
./configure --prefix=/usr
make
sudo make install

Avidemux should now be full speed again!

---

### Post by Mateo on 2007-04-26
thanks, i'll give this a shot.  I never used avidemux in Edgy, but in Feisty it takes me about 2 hours to do a 30 minute program.  I think i'd use this more often if it didn't take so long.  i'll give this solution a shot and hope for the best.

---

### Post by Loïc2 on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xvidcore/+bug/84705](https://bugs.launchpad.net/ubuntu/+source/xvidcore/+bug/84705) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Je viens de recompiler le paquet Ubuntu Feisty avec yasm dans les Depends pour i386 - je l'ai testé et le problème est résolu.

Je l'ai uploadé comme attachement au Bug #84705 in xvidcore sur launchpad :

[https://bugs.launchpad.net/ubuntu/+source/xvidcore/+bug/84705](https://bugs.launchpad.net/ubuntu/+source/xvidcore/+bug/84705)

Le lien direct pour le paquet est :
[http://librarian.launchpad.net/7415152/libxvidcore4_1.1.2-0.1ubuntu2%7Eproposed1_i386.deb](http://librarian.launchpad.net/7415152/libxvidcore4_1.1.2-0.1ubuntu2%7Eproposed1_i386.deb)

Mais allez plutôt sur la page du bug, je vais sans doute uploader un autre paquet demain (colonne de gauche, onglet "Bug attachments")

---

### Post by Loïc2 on 2007-04-26
Sorry, I was mistaking it with another tab in Firefox :)

Translation :

I've quickly built a dirty package that fixes the problem - it's the Ubuntu Feisty one compiled with yasm as Depends not only for amd64 but also for i386.

However, it's not signed - I'll try to find my key tomorrow (laaate now) and upload a prefect one.

Except for that everything works - I've gone from 2 fps to 15 fps (2nd pass). It depends on yasm now, so if dpkg complains just :
sudo apt-get install yasm

Go get it at:
[https://bugs.launchpad.net/ubuntu/+s...ore/+bug/84705](https://bugs.launchpad.net/ubuntu/+s...ore/+bug/84705)

Direct link:
[http://librarian.launchpad.net/74151...osed1_i386.deb](http://librarian.launchpad.net/74151...osed1_i386.deb)
(But since I might upload another version tomorrow, it might be better to go on the bug page then click "Bug attachments" on the left column.

---

### Post by Mateo on 2007-04-26
thanks a lot Loic2.  Tell me, did you build this from source the way yanewby said to do?  I did that, but haven't tried to encode yet to test.

---

### Post by Loïc2 on 2007-04-29
No, I built it using the ubuntu source package, only had to coorect the mistake in debian/control to add yasm in the Build-Depends.

You can use it "as an Ubuntu package".

The fixed package is already in -proposed (eneble it in the repos, and in the updates that will be proposed only install it (but not the other updates) then deactivate -proposed.

Then please test it and reply to the bug with "works for me" (if it works) precising you installed it from the ubuntu feisty -proposed repo.

We need 2 people saying that it works for them before next Saurday, then the package will be moved to universe and everybody will benefit from it by normal update process :)

---

### Post by disturbedite on 2007-04-29
it worked fine for me on feisty, but now i've uprgrade to gutsy and it still works fine.  (oh, i'm kubuntu too btw).

---

### Post by Mateo on 2007-04-29
i don't understand what you mean about how to install it.  I have the proposed repo.  What do I do now.  what is the name of the package.

---

### Post by Mateo on 2007-05-24
So, xvid works fine, but x264 is extremely slow, like 7fps on the first pass.  Any way to fix that?

---

