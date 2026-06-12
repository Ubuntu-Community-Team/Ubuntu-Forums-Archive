---
title: "Black screen of death."
date: 2009-03-04
forum: Multimedia Software
---

### Post by minhamra on 2009-03-04
Hello all, 

Seriously annoying intermittent issue:
somewhere between 30 minutes and 30 hours the screen goes black. I have not been able to correlate the issue with an activity although I am usually in Firefox. 

I hit Ctrl-F1 and try startX but it tells me the server is still runing and I need to clear the lock on a file. Tried that but no joy. 

Any tips on how I could turn on loging of X or something to get to the bottom of this would be most welcome. 

Dell aptitude 410 laptop
Ubuntu Intrepid Ibex
lspci returns the following
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Thanks.

---

### Post by NT4usB on 2009-03-04
If you want to restart display manager:
```
sudo /etc/init.d/gdm stop (or start or restart)
```
x keeps a log if you want to look at it:```
cat /var/log/Xorg.0.log
```
There are options you can add to xorg.conf to make the log more verbose but I can't recall what they are...

---

### Post by minhamra on 2009-03-05
Thank you .....perfect.

---

