---
title: "Problem with k3b burning cd-r's"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by ninthforce on 2007-10-13
hey guys my burner is on the fritz.....

k3b wont let me burn anything! i click "burn" and select the parameters then try to burn and it fails
giving me the error:

IO Error: most likely no space left on harddisk.

DEBUG INFO:
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-386
Devices
-----------------------
_NEC DVD+-RW ND-3650A 105C (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]



any suggestions? 
I have more than enough space left look at this

red-clover@98:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
_**/dev/sda7              79G   26G   49G  35% /**_
varrun                505M  140K  505M   1% /var/run
varlock               505M  4.0K  505M   1% /var/lock
procbususb            505M  164K  505M   1% /proc/bus/usb
udev                  505M  164K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   34M  472M   7% /lib/modules/2.6.20-16-386/volatile
/dev/sda2              59G   58G  1.6G  98% /media/Data
red-clover@98:~$

any ideas?

---

### Post by bodhi.zazen on 2008-07-19
I see this is an old post, sorry about that.

There is a bug report with a work around here :

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/103075)

Hopefully that information will help you or anyone who finds this thread via google / search :)

---

