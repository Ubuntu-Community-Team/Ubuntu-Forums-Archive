---
title: "irrecord not  showing anything however mode2 does"
date: 2010-05-04
forum: Multimedia Software
---

### Post by rusmnicolae on 2010-05-04
1st i want to apologize, i  just realize the  this  is not the right place for this  issue.

I did manage to install lirc  until the  step where 

 mode2 -d /dev/lirc0 

is  showing stuff when  a remote  has a button pressed  

First I did a try with     

include /usr/share/lirc/remotes/samsung/lircd.conf.samsung

in lircd.conf because  one my remote is samsung, however when irw  failed to show anything i did try to record with irrecord  

However  irrecord refuse to  find anything when i m using it
As long as i m pressing buttons  it stays there, and when i give up, it ends  after like a few seconds with the following:                                                       

Press RETURN now to start recording.  
irrecord: no data for 10 secs, aborting  
irrecord: gap not found, can't continue                                                          

mode2 gives  the following, and just for 1  button pressed for about 1 sec : 
root@MainDataTank:~# mode2 -d /dev/lirc0 
pulse 12340259 
space 9106 
pulse 4401 
space 650 
pulse 480 
space 629 
pulse 478 
space 658 
pulse 473 
space 653 
pulse 479 space 630 pulse 478 space 654 pulse 478 space 651 pulse 478 space 629 pulse 476 space 658 pulse 1611 space 622 pulse 482 space 650 pulse 1610 space 634 pulse 1606 space 652 pulse 479 space 627 pulse 1609 space 656 pulse 1584 space 653 pulse 1614 space 623 pulse 1613 space 651 pulse 476 space 632 pulse 476 space 654 pulse 478 space 652 pulse 483 space 625 pulse 479 space 654 pulse 474 space 654 pulse 478 space 634 pulse 474 space 644 pulse 1626 space 624 pulse 1607 space 654 pulse 1583 space 657 pulse 1608 space 628 pulse 1612 space 650 pulse 1588 space 651 pulse 1612 space 628 pulse 42013 space 9107 pulse 2171 space 619 pulse 95929 space 9106 pulse 2157 space 633 ^C     

Ty for any advice or help u can offer as i m stuck with this.

---

