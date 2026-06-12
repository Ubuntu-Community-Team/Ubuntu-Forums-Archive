---
title: "X + new kernel (2.6.15-25) = trouble"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by woot on 2006-06-16
well, today, autoupdate, up2 new kernel (2.6.15-25), i install, reboot, and as expected x doesnt starts anymore

at the previous update i had to re-install nvidia-glx nvidia-kernel-common
which requireds also linux-restricted-modules-2.6.15-25-386, though in the repos only linux-restricted-modules-2.6.15-23-386 is avaible, so i reinstalled but all in vain, im still running the *old* kernel, do i just have to be patient? or what should i do to run the new kernel and a working x (running gnome)

---

### Post by givré on 2006-06-16
try to update again, probably that it was not upload yet in your mirror serveur. (i have the new linux-restricted-modules-2.6.15-25-386) .
If not, let see your /etc/apt/source.lst

---

### Post by woot on 2006-06-16
I (running my previous kernel) dit sudo apt-get update (to refresh packaging)
and then i dit sudo apt-get install linux-restricted-modules-
and hit tab (to see what he has to offer me and the -25 is still not in it...


```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://be.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://be.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://be.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free
```

---

### Post by givré on 2006-06-16
If you go there [http://archive.ubuntu.com/ubuntu/pool/restricted/l/](http://archive.ubuntu.com/ubuntu/pool/restricted/l/)
you will have it, i don't know why you don't have it yet (it's probably not yet in the be mirror.

Three soluce:
-Change your source.lst to have the main mirror : delete be. from all your link
-Take it from the main mirror
-Wait until it's upload (shouldn't be longer than 1 day)

---

### Post by woot on 2006-06-16
ill just manual dl and install it :)

weird that i didnt see it on ubuntu.packages.com :)

but o well, no panic though, I knew it was a matter of time :)

thnx for helping me out to the right place

---

