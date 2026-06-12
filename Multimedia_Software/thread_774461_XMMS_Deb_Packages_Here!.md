---
title: "XMMS Deb Packages Here!"
date: 2008-04-29
forum: Multimedia Software
---

### Post by DirtDawg on 2008-04-29
I keep tripping over people requesting xmms player for various reasons where Audacious just does not cut it. I'm not sure what prompted the removal of xmms and bmp from the Hardy repos, but in the meantime, there are deb packages of xmms available. Thanks to fellow forum member JimmyHopkins for the tip.

Go to this web address: [https://launchpad.net/ubuntu/hardy/+package/xmms](https://launchpad.net/ubuntu/hardy/+package/xmms)

On the left hand side, expand the "Published as" menu and click on your architecture ("xmms 1:1.2.10+20070601-1 in i386 (Release)" for example)

This will send you to a page with a deb package under the heading "File download" along with a list of dependencies.

Hope this proves useful.

UPDATE: The AMD64 Deb the above link points to is faulty, but Temüjin was nice enough to [Provide a solution]("http://ubuntuforums.org/showthread.php?p=5466332&highlight=xmms#post5466332"). Thanks Temüjin!

UPDATE: Forums member Mariuz has kindly made .debs for Ibex available [here]("https://edge.launchpad.net/~mapopa/+archive/+index?field.name_filter=xmms&field.status_filter=published"). I have not tested these, so use them at your own risk. If someone tries Mariuz's packages, please post your experiences at the end of this thread. Thanks Mariuz!

---

### Post by szako on 2008-04-30
Thanks :) Was looking for it

---

### Post by Zerocool10482 on 2008-05-10
I got the file but now I need something to install it. But thanks for the link. I'll get it to work.

---

### Post by elfuego on 2008-05-10
Thanks a lot! It was a few hours bother to get xmms back - but it's back and running. :KS

---

### Post by j0mpa on 2008-05-14
I get an error message when i installed it saying that open a console and run "sudo apt-get install -f" And then ubuntu starts to remove xmms?
What should i do ?

---

### Post by DirtDawg on 2008-05-14
> **j0mpa said:**
> I get an error message when i installed it saying that open a console and run "sudo apt-get install -f" And then ubuntu starts to remove xmms?
What should i do ?

"sudo apt-get install -f" removes partially installed packages. Usually this happens when you are missing files the deb package depends on. Make sure you have all the packeges listed under "depends on" before you install the xmms deb.

---

### Post by styphon on 2008-05-15
Whenever I run this I get the error message:
```
Error: Dependency is not satiafiable: libglib1.2
```
I've checked that all of the dependancy's specified are installed. I also used sudo apt-get install on all of the ones listed.

Please help a nwebie to linux get to grips with installing XMMS

---

### Post by DirtDawg on 2008-05-15
> **styphon said:**
> Whenever I run this I get the error message:
```
Error: Dependency is not satiafiable: libglib1.2
```
I've checked that all of the dependancy's specified are installed. I also used sudo apt-get install on all of the ones listed.

Please help a nwebie to linux get to grips with installing XMMS

The package name is slightly different. Try:
```
sudo apt-get install libglib1.2ldbl
```

---

### Post by lardbit on 2008-05-15
I receive the same message when trying to install the deb package from launchpad. saying that libglib1.2 dependency is not met. 

but when i do a 

sudo apt-get install libglib1.2-dev libglib1.2ldbl

i get ...

libglib1.2-dev is already the newest version.
libglib1.2ldbl is already the newest version.

thoughts?

---

### Post by lardbit on 2008-05-15
UPDATE to my previous post above:

I gave up with the deb packages and compiled the source. Go here to these dandy instructions for the  newest version 1.2.11 (the launchpad deb package was 1.2.10):

[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

worked perfectly.

makes me sad they removed it from the repos :(

---

### Post by styphon on 2008-05-16
> **lardbit said:**
> UPDATE to my previous post above:

I gave up with the deb packages and compiled the source. Go here to these dandy instructions for the  newest version 1.2.11 (the launchpad deb package was 1.2.10):

[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

worked perfectly.

makes me sad they removed it from the repos :(

Worked great for me too. Thanks.

---

### Post by bengoza on 2008-06-10
For those of you that don't want to compile from source:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

No unresolvable dependencies!

---

### Post by Mr.Auer on 2008-07-26
Thanks a thousand times!
I was just looking for XMMS for my Eee pc, since I switched Ubuntu-eee on it. Audacious tends to skip audio at times when under heavy load - Ive noticed this on other slower comps as well, like my ancient Thinkpad a21m - think 192 mb / 500 mhz sweetness :) But XMMS works like a charm on that one too.

---

### Post by markbuntu on 2008-07-26
The unresolvable dependencies only happen with the 64 bit install.

---

### Post by Yellow Pasque on 2008-07-27
The amd64 .deb file was poorly built (in addition to referring to a now obsolete package). I fixed the dependencies and directory scheme.

The patched .deb package is too large to host on these forums and I don't know whom or what mailing list to send the file to.

In the mean time, if you're interested in the .deb, PM me and I'll send it to you.

---

### Post by markbuntu on 2008-07-27
I got around the amd64 deb problem in some weird confusing late night manner I can't remember but thanks anyway for fixing that.

---

### Post by TusharG on 2008-07-28
Thanks a ton... I really wonder why this package has been removed! Other mp3/music players are good but not as slick as this one...

---

### Post by dagoss on 2008-08-13
Does anyone know why this package was removed?  It seems strange as I was under the impression that it's a fairly popular program.

---

### Post by jasonwatkins on 2008-09-16
thought i'd come back here as it's the logical point.

is there any way of getting the xmms-mp4 plugin working in hardy ?

i'm having trouble convincing it that libglib is up to date :)

---

### Post by Yellow Pasque on 2008-09-17
> **dagoss said:**
> Does anyone know why this package was removed?  It seems strange as I was under the impression that it's a fairly popular program.
If you're cynical, you'll find this amusing...
[http://thread.gmane.org/gmane.linux.debian.devel.general/116761](http://thread.gmane.org/gmane.linux.debian.devel.general/116761)

---

### Post by dualpretop on 2008-09-17
XMMS is former!:)

[http://ubuntuforums.org/showthread.php?p=5773714](http://ubuntuforums.org/showthread.php?p=5773714)

---

### Post by anv on 2008-10-01
did anyone have amd64 xmms package?

---

### Post by Yellow Pasque on 2008-10-01
> **anv said:**
> did anyone have amd64 xmms package?
I have an amd64 .deb, but I've been very lazy about getting my web page up and hosting it.

---

### Post by mariuz on 2008-11-21
I have added packages for intrepid in my ppa 

[https://edge.launchpad.net/~mapopa/+archive/+index?field.name_filter=xmms&field.status_filter=published]("https://edge.launchpad.net/~mapopa/+archive/+index?field.name_filter=xmms&field.status_filter=published")

also i intend to add an bzr repository where to add the various patches

---

### Post by antmenj on 2008-11-23
This one worked first shot on hardy i386.

[http://launchpadlibrarian.net/11173488/xmms_1.2.10%2B20070601-1build2_i386.deb]("http://launchpadlibrarian.net/11173488/xmms_1.2.10%2B20070601-1build2_i386.deb")

---

### Post by Strid on 2008-12-11
Ahh, works like a charm on 64-bit Ibex here! Added the /etc/apt/sources.list entrys and apt-get'ed xmms and xmms-wma

---

### Post by jastonas on 2008-12-11
I havent really used xmms alot. I had it on ubuntu 7.04 with a skin that made it a lot like winamp, no library though from what i remember. Now i am trying to use xmms2 but that thing is just too hard and i have tried a couple of guis, even adding files are a big big mess with the gui clients!

---

### Post by mituss on 2009-06-12
for xmms x32x64...
"sudo gedit /etc/apt/sources.list"
then add those lines at the end of the files

"deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse"

no authentic... key req..
then just use the basic
"sudo apt-get install xmms"
in case of some interf..
"sudo apt-get install xmms --fix-missing"
thats all fox :D :-({|=

---

### Post by DirtDawg on 2009-06-13
> **mituss said:**
> for xmms x32x64...
"sudo gedit /etc/apt/sources.list"
then add those lines at the end of the files

"deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse"

no authentic... key req..
then just use the basic
"sudo apt-get install xmms"
in case of some interf..
"sudo apt-get install xmms --fix-missing"
thats all fox :D :-({|=

If this method worked for you that's great. However, I am going to recommend people do *not* add old repositories to their sources list as there is a chance conflicting repositories could damage their install.

---

### Post by wollac on 2010-03-22
**_Here is a better way to install:_**

**First, open the 'source.list' file:**

sudo gedit /etc/apt/sources.list

**Next, add these two lines, then save and close the file:**

(For ubuntu 9.04 or later):

deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./

_OR_

(For ubuntu 8.04):

deb [http://www.pvv.ntnu.no/~knuta/xmms/hardy](http://www.pvv.ntnu.no/~knuta/xmms/hardy) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/hardy](http://www.pvv.ntnu.no/~knuta/xmms/hardy) ./

**Finally, Update and install xmms:**

sudo apt-get update

sudo apt-get install xmms

---

### Post by philip5 on 2010-03-23
I have XMMS for Karmic on my PPA on Launchpad for anyone interested. See my signture for link to PPA.

Have fun!

---

### Post by gracchus on 2010-03-24
Hey philip5, thanks a lot I love the old school xmms.  Do you know if there is a pulseaudio output plugin for it by chance?

---

### Post by philip5 on 2010-03-24
> **gracchus said:**
> Hey philip5, thanks a lot I love the old school xmms.  Do you know if there is a pulseaudio output plugin for it by chance?
I think there is a pulseaudio plugin for XMMS that I can port and add to my repository. I'll look into it when I get home tonight.

[edit]
Done. Did it right when I got home so you will any time now find the package xmms-pulse on my PPA for Karmic. It's just waiting to be built at the moment...

You can after installation choose pulseaudio as a output plugin for audio in xmms preferences.

Have fun!

---

