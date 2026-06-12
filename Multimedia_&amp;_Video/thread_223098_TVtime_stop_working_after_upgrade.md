---
title: "TVtime stop working after upgrade"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by handband2 on 2006-07-25
I was wondering if anyone could help me...?

Everything worked GREAT before but....

I recently got back from vacation and noticed there was a bunch of updates (included in the update was a new kernel) I needed to install for Dapper.  I went and updated the system.  Now everytime I run TVtime I get No Signal.  

I tried to resort back to the old kernel but I get the same thing, No Signal.

Has anyone else had this problem? or know how to fix it?

I'm running:

Hauppauge - WinTV GO-Plus [http://www.hauppauge.com/pages/products/data_goplus.html](http://www.hauppauge.com/pages/products/data_goplus.html)

Dapper Drake 6.06 (2.6.15-26-386)

Thanks!

---

### Post by DonL on 2006-07-26
Do you have a video camera you can connect to the card to see if it works?
If you have the cable hooked up to a splitter, check all your connections. Can't think of why the card wouldn't work after a change in kernels. I upgrade all the time, and my ATI card just keeps working.
Hope it's something simple.

---

### Post by handband2 on 2006-07-26
I booted my computer with Knoppix (live CD).  The card works fine with Knoppix (live CD).

---

### Post by handband2 on 2006-07-26
Okay, I got it fixed.

Don't know how or why??!!

All I did was boot into windows (I'm running a dual boot system Ubuntu/Windows) started up the program to watch TV.  Eveything worked fine while in Windows.  Shut down Windows and rebooted into Ubuntu.  Now it works PERFECT.
If anyone knows how or why this occurs, could you please fill me in...I'm just curious.

Thanks!!

---

### Post by cblanquer on 2006-12-12
I am going to try this as well. 
As an explanation, it is possible that running it on W has setup anything on the TV card ROM setup , which then remains when restarting it in Linux.
(that would make an awful dependency on W, of course)

---

