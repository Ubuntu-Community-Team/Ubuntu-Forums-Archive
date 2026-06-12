---
title: "[Karmic Koala i386] mouse hangs during high bandwidth downloads"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Shocker on 2010-02-08
Hi there!

My system configuration is the following:

Ubuntu KK (clean install)
CPU AMD Athlon X2 3800+ 
RAM: 1.5 GB
Video card: ATI RADEON X1800 (R520) PCI-E

fdisk -l reports:
/dev/sdb1               1        4664    37463548+  83  Linux
/dev/sdb2            4665        4870     1654695    5  Extended
/dev/sdb5            4665        4870     1654663+  82  Linux swap / Solaris

I'm experiencing this kind of issue:

as I'm starting a download of a large file in Firefox something weird happens: especially if the file can be downloaded with full bandwidth (ADSL2+, 10 MBps), my mouse starts hanging around and I cannot move the pointer smoothly anymore until I manage to set up the file name for the download from the pop-up window of Firefox. Sometimes things don't get better even after the file name setting.

I tried to reproduce the issue but my PC is not always performing in the same way...

I thought of a RAM problem but the last time I did a test (15 days ago) all was ok.

Has anyone experienced the same problem?
Any hint is highly appreciated.

Best regards

Shocker

---

### Post by alexfish on 2010-02-08
hi

you can try starting the Error_Console from Firefox tools section ,this may give an indication of what is happening

regards alexfish

---

### Post by Shocker on 2010-02-09
Hi alexfish,

thank you for your reply.

I opened the error console after it happend again but no error message/warning is reported.

As far as I can understand it seems something related to the memory load/performance...

In case anyone has a suggestion, please write back.

Thanks in advance

Shocker

---

### Post by Shocker on 2010-07-10
I know have installed the Lucid Lynx release but things have not changed.

The problem happens only on high speed downloads, I don't remember if it happens also on Ubuntu updates downloads.

Any hint?

Thanks a lot

Shock99er

EDIT: 

I cleared the error console and tried a download link that was causing the problem. Here is what I get:
AntLog: Rejected =>  url:[http://www.perkinsengines.it/pdfzip%5Cserie1000zip.zip](http://www.perkinsengines.it/pdfzip%5Cserie1000zip.zip) content-type:application/x-zip-compressed

Any suggestion?

END OF EDIT

---

### Post by Shocker on 2010-07-11
New info:

I tried to download the same file:

[http://www.perkinsengines.it/pdfzip%5Cserie1000zip.zip](http://www.perkinsengines.it/pdfzip%5Cserie1000zip.zip)

with the wget command and I got the same issue,

This means that the problem is not caused by Firefox but it's something due to how Ubuntu manages the high bandwidth file transfers.

Hoping that anyone can give some help..

Shock99er

---

### Post by Shocker on 2010-07-12
Bump!

My issue is similar to this one:

[http://ubuntuforums.org/archive/index.php/t-499802.html](http://ubuntuforums.org/archive/index.php/t-499802.html)

but unfortunately I cannot find any error related to irq in the dmes log...

---

### Post by Shocker on 2010-07-15
Bump again...

anyone to give some help?

Nevertheless it seems I'm not really alone with such problem:
[http://ubuntuforums.org/archive/index.php/t-189572.html](http://ubuntuforums.org/archive/index.php/t-189572.html)

Rgds

Shocker

---

### Post by Shocker on 2010-07-20
Hi everybody!

I wanted to tell you I was able to fix the problem.
It seems it was caused by the low charge in the batteries of my wireless keyboard (Logitech ex110). 
In any case check also if your mouse is well plugged in the ps2 port
I realized it was a logitech problem when I tried to simulate the issue with a different ps/2 mouse.

Bye!

Shocker

---

### Post by alexfish on 2010-07-20
Running for 6 months on flat batteries , that's amazing

Don't know what to say

---

### Post by alexfish on 2010-07-20
hi

done a search in sofware center , found lomoco ,

---

### Post by Shocker on 2010-07-21
> **alexfish said:**
> Running for 6 months on flat batteries , that's amazing

Don't know what to say

Indeed I was really surprised discovering that the batteries on the keyboard can affect this way the mouse signal....

But before yesterday I didn't experience any problem when typing on th the keyboard!

Maybe the previous time I changed the battery without connecting the fact that the mouse started again to behave normally on heavy network downloads...

Time will tell if this was the key of the issue.

Bye

Shocker

---

### Post by Shocker on 2011-02-23
[http://ubuntuforums.org/showthread.php?p=10487963#post10487963](http://ubuntuforums.org/showthread.php?p=10487963#post10487963)

I finally found the reasons of this problem and how to fix (or perhaps reduce) this bad bahavior!

Shocker

---

### Post by alexfish on 2011-02-23
klunk Klik : something just fell into place from Reading the link ;

years ago had a wireless and keyboard of infamous brand , same as the os , same problems , but when changed to different motherboard , the problem disappeared ,
the main reason for the change of motherboard was compatibility issues with the memory

ah well another six months gone,

---

### Post by Shocker on 2011-02-24
Looks like time passes by faster everyday ;)
Bye 

Shocker

---

