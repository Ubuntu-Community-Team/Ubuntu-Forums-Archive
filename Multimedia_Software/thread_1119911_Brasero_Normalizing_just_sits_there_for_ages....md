---
title: "Brasero Normalizing just sits there for ages..."
date: 2009-04-08
forum: Multimedia Software
---

### Post by Flywaver on 2009-04-08
Greetings,

I tried 3x to burn mp3's to a CD and Brasero would start normalizing tracks but it would take ages...even after 2h it was still "normalizing" tracks! This was with 16 small MP3 files! If I disactivate normalizing they burn fine...except that the sound levels are way off.

Anyone got the same issue?

Brasero 2.2.26
Ubuntu Jaunty Beta

Cheers!

---

### Post by Flywaver on 2009-04-08
bump...anyone??

---

### Post by Flywaver on 2009-04-10
bump...seems I am the only one having this issue?

---

### Post by sgosnell on 2009-04-10
Normalizing is a long process.  Getting it done for 3 CDs will take a long time.  I suggest letting it run overnight, and you should get it done eventually.

---

### Post by Flywaver on 2009-04-10
> **sgosnell said:**
> Normalizing is a long process.  Getting it done for 3 CDs will take a long time.  I suggest letting it run overnight, and you should get it done eventually.

uhhh...not 3CD's lol...ONE CD with 16 songs!! That's the scary part! Never had any problem burning such a low amount of mp3's to a CD with Burn4Free under window$.

---

### Post by eric71 on 2009-04-11
There has been a bug filed and confirmed on jaunty for this. It has medium priority, but has not been fixed yet. Been waiting as this is a big one for me. [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/340569](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/340569)

---

### Post by Flywaver on 2009-04-11
> **eric71 said:**
> There has been a bug filed and confirmed on jaunty for this. It has medium priority, but has not been fixed yet. Been waiting as this is a big one for me. [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/340569](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/340569)

Thanks for the heads up!!!
Pretty annoying if you ask me! :)

Cheers!

---

### Post by u-slayer on 2009-04-11
Try using normalize-audio. I can normalize 2 hours of audio in less than a minute using this program.

---

### Post by boxrec on 2009-04-23
Go to plugins and uncheck normalize, this will allow you to burn the tracks.

---

### Post by Pelonchas on 2009-04-28
> **boxrec said:**
> Go to plugins and uncheck normalize, this will allow you to burn the tracks.

Thanx boxrec, this help me out of the problem. So easy solution until they fixed the issue.

---

### Post by Flywaver on 2009-04-28
> **Pelonchas said:**
> Thanx boxrec, this help me out of the problem. So easy solution until they fixed the issue.

That's what I also did...but I ended up with a CD that has such different volume levels :(

Can't wait for this bug to be fixed!

---

### Post by detrate on 2009-05-04
It's doing something...

```
cd /tmp; watch -n 5 -d 'ls -la |grep bra'
```

...but that something takes forever

---

### Post by tsali on 2009-05-31
I'm having this problem also...

Cured it by installing k3b...

---

### Post by Razmear on 2009-06-01
Thanks for the tip about k3b! 
Had the same issue as the OP and k3b worked no problem with excellent quality, and you saved me from testing a bunch of other burners to find the good one! 

eb

---

### Post by jward3010 on 2009-06-03
> **sgosnell said:**
> Normalizing is a long process.  Getting it done for 3 CDs will take a long time.  I suggest letting it run overnight, and you should get it done eventually.

Normalising should only take at worst a few minutes, not hours or even a half hour. MP3 files sound wave can be read in seconds and volume levels can be analysed fast. 

This is a **Brasero bug**, the original bug report is this one in fact: [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/303770](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/303770) - Someone else mentioned a different number but it turned out to be a later duplicate bug, so post all problems in the above bug report (303770).

---

### Post by obieito on 2009-06-18
The link you provide points to a file-deleting related Brasero bug.

I think the correct bug reports are these two:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/373923](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/373923)

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/364027](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/364027)

They both reference the normalize plugin, one from the mp3 converter and other from the audio cd recorder. I posted there debug log, there is another one, in both cases it seems to fail at the second track it's trying to normalize... no solution as of yet.

---

### Post by strungoutfan78 on 2009-07-31
Or one could simply avoid the bug by installing the latest version from the maintainer, which is what I chose to do.  When in doubt compile from source.  I'm now running version 2.27.5 with no issues.  You'll need to install a few dev packages but other than that it's pretty simple.

---

### Post by monkeykong on 2009-08-19
> **strungoutfan78 said:**
> Or one could simply avoid the bug by installing the latest version from the maintainer, which is what I chose to do. When in doubt compile from source. I'm now running version 2.27.5 with no issues. You'll need to install a few dev packages but other than that it's pretty simple.

Nice that it works with newer versions. The error was fixed in Brasero 2.27.4 according to the [release notes]("http://osdir.com/ml/ftp-release-list/2009-07/msg00057.html"). I installed Brasero 2.27.90, later 2.27.5 from source on my Ubuntu Jaunty installation, the following line supplied Brasero with the necessary dev packages:

```
apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libunique-1.0-0 libgconf2-dev libdbus-glib-1-dev
```

Unfortunatily Brasero 2.27.90 and 2.27.5 failed to load my old Brasero audio projects correctly, only the last track reappeared in the list. Brasero 2.27.5 crashed when loading the project saved with Brasero 2.27.90. And 2.27.90 has an UI problem applying actions to a highlighted item in the list to the above item. I'll give up now.

---

### Post by jean noel on 2009-09-25
> **boxrec said:**
> Go to plugins and uncheck normalize, this will allow you to burn the tracks.

I recently had the same problem in burning a rare mp3 cd. That solved the problem. Thanks for the idea.

Jean Noel

---

### Post by missmoondog on 2009-09-26
yep, noticed this instantly on my brand new xubuntu install.

remembering from back in 2006, when i had this same issue, instantly removed brasero and installed k3b. all fixed!!

---

### Post by AyAn4m1 on 2009-10-23
> **boxrec said:**
> Go to plugins and uncheck normalize, this will allow you to burn the tracks.

Easy and perfect solution for me. My albums are normalized anyway. Thanks a ton!

---

### Post by 1roxtar on 2009-10-23
> **Razmear said:**
> Thanks for the tip about k3b! 
Had the same issue as the OP and k3b worked no problem with excellent quality, and you saved me from testing a bunch of other burners to find the good one! 

eb

I use K3B exclusively and removed Brasero entirely on all my Ubuntu machines.  K3b is an awesome burning program and works perfectly with the Gnome desktop even though it was made for KDE.

:guitar:

---

### Post by narcisgarcia on 2009-10-28
This is fixed since the version 2.26.2 of Brasero.

For the moment you can deactivate the "Normalize" plugin in the Edit menu.

---

### Post by wbee on 2009-10-28
Hello,

Here,another endorsement of K3b (from the Synaptic Manager).

---

### Post by ryrules1 on 2009-12-18
suffering from this bug, among other problems. Plus Brasero just takes way to long, going to install K3b.

---

