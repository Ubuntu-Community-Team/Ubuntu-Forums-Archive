---
title: "Broadcom Wireless Issues"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by rogersab1223 on 2009-12-31
Hello all - 

I'm using an HP Pavilion dv4-1283cl which has as Broadcom 4322 wireless chip in it.  I have Ubuntu 9.10 installed.

I'm having 2 problems.

Upon installing Ubuntu, wireless didn't work.  I was able to get the Broadcom driver and, following the instructions, wireless works.  Sorta.  

_____________________________________
Problem 1: 
Even though I've added ssb to blacklist, it still loads.  So I have to 

rmmod ssb
THEN I have to 
modprobe lib80211
insmod wl.ko

To get things working.  

How do I keep ssb from running (as per the directions with the Broadcom driver) AND run the second commands so wireless works from boot.

______________________________________
Problem 2:
Wireless, when working, continues to drop out.  About every minute, I lose the connection and have to wait for it to reestablish.  Then I usually have to reenter the password.  

Obviously, that's not going to work.  What's the issue here?

Thanks in advance for all your help.
Andy

---

### Post by focwiz on 2009-12-31
> **rogersab1223 said:**
> Hello all - 

I'm using an HP Pavilion dv4-1283cl which has as Broadcom 4322 wireless chip in it.  I have Ubuntu 9.10 installed.

I'm having 2 problems.

Upon installing Ubuntu, wireless didn't work.  I was able to get the Broadcom driver and, following the instructions, wireless works.  Sorta.  

_____________________________________
Problem 1: 
Even though I've added ssb to blacklist, it still loads.  So I have to 

rmmod ssb
THEN I have to 
modprobe lib80211
insmod wl.ko

To get things working.  

How do I keep ssb from running (as per the directions with the Broadcom driver) AND run the second commands so wireless works from boot.

______________________________________
Problem 2:
Wireless, when working, continues to drop out.  About every minute, I lose the connection and have to wait for it to reestablish.  Then I usually have to reenter the password.  

Obviously, that's not going to work.  What's the issue here?

Thanks in advance for all your help.
Andy


See the following post...?
[http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699")

---

