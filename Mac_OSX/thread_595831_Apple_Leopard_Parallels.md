---
title: "Apple Leopard Parallels"
date: 2007-10-29
forum: Mac OSX
---

### Post by darrenm on 2007-10-29
Argh I'm really wound up about the press Leopard is getting with Parallels. 

It enables Mac users to run Windows applications seamlessly on their desktop. Sounds great but you still need a copy of Windows installed in VMware fusion to make it work.

Right.... so its basically what Linux users have been able to do for about 18 months but it wasn't that great a feature until Apple "invented" it.

Steps to getting it to work in Linux:

1. Install Windows in VMware
2. copy seamlessrdpshell.exe into Windows
3. Make a shortcut on your Linux desktop called Internet Crapsplorer
4. Give the shortcut a command line of "rdesktop -A -s "c:\seamlessrdpshell.exe c:\program files\internet explorer\iexplore.exe" an.ip.addr.ess"
5. Click link and 'enjoy' Internet Crapsplorer

---

### Post by kragen on 2007-10-29
So? thats kind of what Apple do - take cool features that arent available on other OS's, make them really slick, and then market them really well.

Take the Time Machine for example, I believe it already existed under linux in some form or other before it did on OSX - Apple simply saw that they could market this as a really cool unique feature, and put a lot of effort into making sure it was really polished, and then put a fair amount of effort into showing it off it with cool shiny screenshots.

You have to hand it to them really - the new "Stacks" feature isnt even that useful but theyve still managed to get every mac user going "wow, thats going to be really cool, I can't wait!!!", just because the stack of icons has a cool looking bendy effect to it! :P

---

### Post by Polygon on 2007-10-29
there is no linux version of 'time machine'...but all it really is is just a bunch of incremental backups (which can be done with a lot of linux programs already) that are essentially time stamped, and a database of what files existed on what date. Im sure this is very possible if some guy wanted to make a time machine clone for linux/windows (which would be pretty cool)

---

### Post by DalekClock on 2007-10-29
Also, Apple doesn't own Parallels. They're a separate company who are credited for creating the integrated virtual desktop feature and selling it as part of their Mac VM software.

---

### Post by Kingsley on 2007-10-29
If Apple is making it seem new and innovative, they're obviously doing something right.

---

### Post by kragen on 2007-10-30
> **Polygon said:**
> there is no linux version of 'time machine'...but all it really is is just a bunch of incremental backups (which can be done with a lot of linux programs already) that are essentially time stamped, and a database of what files existed on what date. Im sure this is very possible if some guy wanted to make a time machine clone for linux/windows (which would be pretty cool)

There are versioning file systems, which are very cool - I didnt really understand how the apple time machine worked, I didnt realise it used an external hard drive, so it really isnt that hard to do, you just need the fancy GUI.

Versioning file systems are cooler though :P

---

### Post by bash on 2007-10-30
> **Polygon said:**
> there is no linux version of 'time machine'...but all it really is is just a bunch of incremental backups (which can be done with a lot of linux programs already) that are essentially time stamped, and a database of what files existed on what date. Im sure this is very possible if some guy wanted to make a time machine clone for linux/windows (which would be pretty cool)

Uhm ... so what do you consider [this](https://wiki.ubuntu.com/TimeVault)? Oh no wait its called Timevault. Can't be the same ;)

You find the Forumthread about it here:

[http://ubuntuforums.org/showthread.php?t=474973](http://ubuntuforums.org/showthread.php?t=474973)

Screenshots here:

[https://wiki.ubuntu.com/TimeVault/ScreenShots](https://wiki.ubuntu.com/TimeVault/ScreenShots)

Download link for .debs:

[https://launchpad.net/timevault/+download](https://launchpad.net/timevault/+download)

---

### Post by inversekinetix on 2007-10-30
leopard comes with free cologne and hair gel.

---

### Post by XENOR on 2007-11-07
Having tried leopard I can only say Ubuntu 7.10 and Tiger are THE OS'
ALLOWED in this house!GG #1!Chase the alley cat out the door!-Xe:mrgreen:

---

### Post by stmiller on 2007-11-07
There is another time machine clone for Linux:

[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

All of the various rsync tools to do this in Linux are there. I imagine projects like this will become polished and merged into distros very soon.

Rsync can work across any network shares, or to anywhere else on the internet! So make backups to off-site servers, etc. Lots of possibilities.

---

### Post by K.Mandla on 2007-11-07
Moved to Mac OSX forum.

---

### Post by BDNiner on 2007-11-07
I have been using rsync for about a year now at work. time machine seems to do the exact same thing but with a GUI, but doesn't it force you to use an external hard drive?

---

### Post by TheWizzard on 2007-11-09
> **Polygon said:**
> there is no linux version of 'time machine'...

excuse me. dirvish was there before apple's time machine
[http://www.dirvish.org/](http://www.dirvish.org/)

---

### Post by Alfa989 on 2007-11-09
> **TheWizzard said:**
> excuse me. dirvish was there before apple's time machine
[http://www.dirvish.org/](http://www.dirvish.org/)

Dude

You do not seriously think that they're the same thing (or even close), right?

---

### Post by TheWizzard on 2007-11-10
> **Alfa989 said:**
> Dude

You do not seriously think that they're the same thing (or even close), right?

"A dirvish backup vault is like a time machine for your data."
this was on the dirvish website before apple announced their time machine. and apple's time machine is nothing but a polished version of dirvish. i'm pretty sure steve jobs borrowed the idea from dirvish.

---

### Post by DalekClock on 2007-11-10
> **BDNiner said:**
> I have been using rsync for about a year now at work. time machine seems to do the exact same thing but with a GUI, but doesn't it force you to use an external hard drive?

You can use other means such as burning backup images to an optical disc or creating a seperate partition, both with their disadvantages(the former makes you take out the disc you're using and the latter bites at your main storage space).

As for Dvirish, I'm not sure even Apple would have herd of it. After all, they usually overlook anything that's not major and the two apps being the same but slightly different is probably just down to coincidence.

As for the other two that have been suggested as Apple's base for Time Machine, neither can be. The first one(Time Vault) was created long after Apple first announced the Time Machine feature and the second one(FlyBack) is referred to by the developers as "Apple Time Machine for Linux".

---

### Post by Alfa989 on 2007-11-10
> **TheWizzard said:**
> "A dirvish backup vault is like a time machine for your data."
this was on the dirvish website before apple announced their time machine. and apple's time machine is nothing but a polished version of dirvish. i'm pretty sure steve jobs borrowed the idea from dirvish.
I'm asking

Can Dirvish restore individual files from the file manager, photo gallery, agenda, etc? :)

---

### Post by TheWizzard on 2007-11-10
> **Alfa989 said:**
> I'm asking

Can Dirvish restore individual files from the file manager, photo gallery, agenda, etc? :)

as far as i know all time machine style backup (including dirvish) stems from: 
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

this is what i use. and yes, you can restore individual files.

---

### Post by Chrisj303 on 2007-11-10
> **darrenm said:**
> Argh I'm really wound up about the press Leopard is getting with Parallels. 

It enables Mac users to run Windows applications seamlessly on their desktop. Sounds great but you still need a copy of Windows installed in VMware fusion to make it work.


Why would it wind you up?


And I don't understand why your saying that you need Windows installed in Vmware fusion for Parallels to work - Fusion and Parallels are two different products.

Parallels desktop is a very good, polished piece of software. It allows me to run both my Vista and Ubuntu **partitions** as virtual machines - right here on my OSX desktop.

"Coherence" mode is also very cool.

Parallels desktop for Linux is also available - it may not be quite as feature heavy as the Mac version, but it is very good.


Mac users can run .exe files without the need for installing Windows - its a piece of software called "Crossover". Its not perfect, but its just as good as Wine.

---

