---
title: "ubuntu 8.04 - k3b burn successful, verify fails"
date: 2009-10-01
forum: Multimedia Software
---

### Post by wbryan01 on 2009-10-01
There has been a problem with K3b doing a verify and the verify fails.  When you manually check the validity of the burn, it is ok.  So burn ok,  verify fails.
This problem appeared in 8.04.  7.10 works as expected.

Problem seen with burning iso's.  Assume same will happen with regular projects.

Reading on the internet, this problem has been linked to the kernal, not k3b.
Is there a work-around or has this been fixed.  Please provide details on on either 
item ( work-around or fix ).

I am running 8.04.2 ubuntu load with kubuntu desktop loaded on top
Here is uname -a to provide kernal/platform details

Linux ubuntu 2.6.24-24-generic #1 SMP Sat Aug 22 00:30:49 UTC 2009 x86_64 GNU/Linux

k3b was 1.04 ( something )
I updated to 1.0.51.

I tried 9.04 and manual verify shows that burn was bad.  So worse.  
I prefer to run 8.04 since it is an LTS.

Any help would be appreciated.
thank you

---

### Post by bruno9779 on 2009-10-01
I have a similar issue with K3B

If i tick the "verify" option, when it finishes writing it ejects the DVD, than close the drawer right away, than k3b simply freezes

---

### Post by cor2y on 2009-10-01
In k3b options disable having the tray eject but leave verification on.
So Settings->Configure k3b->Advanced->Miscelllaneous->Do Not Eject Medium after write process (make sure its checked)

---

### Post by HappyFeet on 2009-10-01
If this happens all the time, then yes, it is probably a software issue. But if it's only once in a while, it could be a bad disc. It *does* happen. CD's are not always perfect either.

---

### Post by wbryan01 on 2009-10-01
I am having the issue that is the kernal issue.
No lockup of k3b.
Just good burn but verify works
( I mean good burn by running cksum on the disk after burn and on the iso file and compare -  they compare so good burn but k3b fails on verify ).

I did not try the no eject because I am afraid that the data is cached and the verify may be invalid.

there was a posting that said that this was fixed for x86 but not AMD64.


I will try try the no-eject to see if works

---

### Post by wbryan01 on 2009-10-01
on 8.04,
I burned the ubuntu 7.10 onto cd with no eject.
k3b failed verify 
my script for verify failed after burn ( with no eject )
I then ejected and ran my verify script again and I got good results ( same disk )
So, the no eject did not work
k3b failed when the burn was good - and so did my script if I do not eject.

To repeat, this looks like the kernal problem problem reported on other bug reports.
I am looking for info from the Ubuntu support team.

---

### Post by wbryan01 on 2009-11-15
Sad that the Ubuntu developers did not reply.
But here is the latest news. Looks like the DVD burn issues have been resolved in Ubuntu 9.10.
I have not tested doing a dvd burn of indidual files, but I have burned cd and dvd iso's with success.
I can say that the version of k3b has been updated.  Not sure if fix came from them or from kernal
updates, but the issue is over for me.

---

