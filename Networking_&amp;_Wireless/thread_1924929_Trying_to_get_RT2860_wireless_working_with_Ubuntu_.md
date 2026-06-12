---
title: "Trying to get RT2860 wireless working with Ubuntu 10.10"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by JohnFDay on 2012-02-13
I've looked through the existing postings and am rapidly reaching the conclusion that "I can't get there from here"....but I'll ask anyway.

I'm trying to get my RT2860 built-in wireless to operate with Ubuntu 10.10.  I have an HP Pavilion P7-1007c PC running Windows 7 and Ubuntu.

The wireless works flawlessly under Windows, but when I try to do anything with it in Ubuntu, I can't even get the "WIRELESS" line to show up in the network manager.  All it shows is "Enable Networking" and  "Enable Notifications".

I'm guessing that I'm missing something quite basic here, but I'm at a complete loss as to how to get this wireless working.

Any ideas will be appreciated!

J. Day

---

### Post by chili555 on 2012-02-13
Please open a terminal and run and post:```
dmesg | grep -i rt2
lspci -nn | grep 0280
lsmod | grep rt2
```Thanks.

---

### Post by JohnFDay on 2012-02-13
Okay, here are the responses that I got...


john@john-p7-1007c:~$ dmesg | grep -i rt2
john@john-p7-1007c:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: RaLink Device [1814:5390]
john@john-p7-1007c:~$ lsmod | grep rt2
john@john-p7-1007c:~$

---

### Post by chili555 on 2012-02-13
> 02:00.0 Network controller [0280]: RaLink Device [1814:5390]Your device is supported by rt2800pci (probably with a firmware upgrade) in Ubuntu 11.10. It can be supported by compiling from source in 10.10; here is an example: [http://ubuntuforums.org/showthread.php?t=1855675](http://ubuntuforums.org/showthread.php?t=1855675)

Which would you rather do, compile from source or upgrade to 11.10? I will be glad to help in either case.

---

### Post by JohnFDay on 2012-02-13
> **chili555 said:**
> Your device is supported by rt2800pci (probably with a firmware upgrade) in Ubuntu 11.10. It can be supported by compiling from source in 10.10; here is an example: [http://ubuntuforums.org/showthread.php?t=1855675](http://ubuntuforums.org/showthread.php?t=1855675)

Which would you rather do, compile from source or upgrade to 11.10? I will be glad to help in either case.

I tried 11.04 and 11.10...couldn't even get the screen to work...so I UN-installed it and went back to 10.10.

Therefore, it looks as if I'll have to try to work with the compiling.

I definitely do appreciate the input!  I'm going to go to that site you supplied and see what, if anything, comes out the other end.  I'll get back to you ASAP.

---

### Post by JohnFDay on 2012-02-13
> **JohnFDay said:**
> I tried 11.04 and 11.10...couldn't even get the screen to work...so I UN-installed it and went back to 10.10.

Therefore, it looks as if I'll have to try to work with the compiling.

I definitely do appreciate the input!  I'm going to go to that site you supplied and see what, if anything, comes out the other end.  I'll get back to you ASAP.

Okay, I've looked at it and tried the first 3 commands...nothing worked.

I'm a real babe in the woods when it comes to Ubuntu...just in case there was any doubt!

---

### Post by chili555 on 2012-02-13
Babes R Us!

Can you get a temporary ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```Then try the compile again. If it won't work, post back the errors.

---

### Post by JohnFDay on 2012-02-14
> **chili555 said:**
> Babes R Us!

Can you get a temporary ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```Then try the compile again. If it won't work, post back the errors.
==================================================================

I have given up.  I re-installed Ubuntu 11.04...or, rather, tried to re-install it.  After booting from the ISO, it went to a black screen and would go no farther.  I then tried booting up from a newly-created Ubuntu 11.10 ISO.  It did the same thing.  In fact, the entire boot process was dead.  Don't know why, and don't particularly care anymore.

To get my computer to boot up once again, I had to do a complete reload of my Windows, then re-loaded Ubuntu 10.10.

Now I'm back up and running again.  I'm no longer going to pursue getting the wireless to work...as long as my ethernet connection is Okay, that's all that really matters.

The only thing I can figure out (after trying Ubuntu 11.-- at least 4 times now, with bad results every time, is that this computer of mine (for whatever indefinable reason) just doesn't like 11.ANYTHING.

Thanks for your kind offer for help.  I'm ending the search here.  A saying from a long time back goes...."If it ain't broke...don't fix it."
Ubuntu 10.10 works (other than the wireless) and it works well.  I'm going to stay with it.  Maybe when Ubuntu 12.something comes along, I'll try again.

Thanks.
John Day

---

