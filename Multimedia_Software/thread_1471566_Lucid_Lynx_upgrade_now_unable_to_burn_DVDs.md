---
title: "Lucid Lynx upgrade: now unable to burn DVDs"
date: 2010-05-03
forum: Multimedia Software
---

### Post by caliburn on 2010-05-03
Applied the Lucid Lynx 10.04 over the weekend.
Since then - I am unable to burn DVDs, although I can successfully read DVD's. 
Everything worked fine before the upgrade.
Under Lucid Lynx I am able to burn CD's (both data files and .ISO) so it isn't the hardware.

I have tried Brasero and k3b as burners - they issue messages that the burner doesn't like the medium, which is standard  DVD-R.
Bear in mind that I could burn similar DVDs *before* the upgrade...

Any help or suggestions on how to fix this please?

---

### Post by bcbc on 2010-05-03
If you had medibuntu repositories beforehand, they get disabled with a new release. My flash stopped working after the upgrade - haven't got around to fixing it but I guess you need the restricted extras again.

---

### Post by caliburn on 2010-05-03
Hi there, enabled the medibuntu repositories and re-installed (and upgraded) libdvdcss, then restart... no joy :( Same error message. Any other suggestions please? The alternative will be to go back to 9.10...

---

### Post by RavanH on 2010-05-03
not sure if it is related but i just tried to make a mirror image from a regular CD with brasero but it fails in every respect... installed all the required extra packages but still no dice 

other threads that might be related:

[http://ubuntuforums.org/showthread.php?t=1471350&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1471350&highlight=brasero)

[http://ubuntuforums.org/showthread.php?t=1468585&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1468585&highlight=brasero)

[http://ubuntuforums.org/showthread.php?t=1470029&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1470029&highlight=brasero)

seems completely messed up :(

---

### Post by caliburn on 2010-05-03
This is a real shame, because other than this I think 10.04 is pretty damn good... but I need this capability. It is *definitely* a Lucid Lynx issue - as I've said, this was all working on Saturday *before* the upgrade. Nothing else has changed.

---

### Post by caliburn on 2010-05-03
Have since disconnected the DVD writer and attached it to Windows. The same DVD writer and a DVD that Lucid had problems with works fine under Windows.

Methinks it is a Lucid specific issue people!

---

### Post by RavanH on 2010-05-03
Found an interesting post here:
[http://ubuntuforums.org/showpost.php?p=4902376&postcount=41](http://ubuntuforums.org/showpost.php?p=4902376&postcount=41)

It might just be the thing that will solve this issue too... Have not got the time for it now but will test it tomorrow ! Unless anyone else wants to try and report about it of course :)

---

### Post by marcellux on 2010-05-03
> **caliburn said:**
> Hi there, enabled the medibuntu repositories and re-installed (and upgraded) libdvdcss, then restart... no joy :( Same error message. Any other suggestions please? The alternative will be to go back to 9.10...

What is exactly the error message you get?

Have you tried setting the "auto speed" to the slowest?

---

### Post by caliburn on 2010-05-04
> **marcellux said:**
> What is exactly the error message you get?

Have you tried setting the "auto speed" to the slowest?

Hi there, the exact message is:

Brasero closed with an unknown error.

I've tried setting auto speed to the lowest speed. It doesn't work. 

Bear in mind the same DVD writer (and DVD's from the same spindle) worked fine pre-Lucid.

---

### Post by sieve on 2010-05-21
> **caliburn said:**
> this was all working on Saturday *before* the upgrade. Nothing else has changed.

Same here.  Had no problems with Brasero in 9.10 before upgrading to 10.04.  I hope someone finds a solution. :confused:

ETA: Just burned several CDs using Brasero on an identical model computer running 9.10

---

### Post by rawdmon on 2010-06-05
Has anyone been able to figure this out?  Ever since the upgrade I can read CDs/DVDs and USB drives, but I can't actually write to them.  There is obviously some sort of permissions issue.

*** EDIT ***: I was able to burn a DVD using brasero instead of CD/DVD creator.  I still have problems with USB drives, but I've just been using the commandline as root to write to those.  This really does need to be fixed.

---

### Post by jasond496 on 2010-06-12
Just a bump and a "me too" here.  I can't burn in brasero, k3b, or gnomebaker.  Brasero and K3b both fail to even recognize that I have optical devices, and gnomebaker seems to be failing with a nondescript error.  It's a 64 bit machine, running the 64 bit flavor of ubuntu, if that matters.

Same deal though, I was burning cds last week on this machine running 9.10.

---

### Post by denchriste@yahoo.com on 2010-06-17
I can not burn dvd or even copy them with lucid 64 bit, worked fine with 9.04... any thoughts ? regards

---

### Post by johnston_evo3 on 2010-07-08
I'm having the same problems.  Anyone came up with a fix yet before I have to delete a lot of stuff to go back to 9.04 :(

---

### Post by marcellux on 2010-07-17
I could not find any solution anywhere! setting the auto speed to the lowest speed just allowed me to burn DVD's up to 1,5 GB size! if the IMAGE file is larger than that, I get the same error message!

with 8.10 I had not that problem! Now I am using 10.04 and still the same problem like 9.04 and 9.10! 

what surprises me is, I re-installed all over again, this time also with an extra partition for WIN XP PRO SP2, and it is not burning DVD's over 1,5 GB either. it is so weird.

---

