---
title: "Live CD does not boot"
date: 2010-11-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-11-10
I tried this on both i386 on a ATI laptop and a amd64 desktop. Both had the same error message:
***Live CD does not boot: mounting aufs on /root failed: No such device ***

There's already a bug reported on the issue:

[https://bugs.launchpad.net/ubuntu/+bug/673527](https://bugs.launchpad.net/ubuntu/+bug/673527)

---

### Post by dino99 on 2010-11-10
hm, testing live cd so early is quite useless

---

### Post by VMC on 2010-11-10
> **dino99 said:**
> hm, testing live cd so early is quite useless

The fact that the LiveCD is there, is meant to be tested, is it not.

---

### Post by Catharsis on 2010-11-10
From yesterday's [Kernel Team Meeting Minutes](https://wiki.ubuntu.com/KernelTeam/Meeting/2010-11-09):

> Work is ongoing to get aufs2 working again so we can have performant live-cds shortly; likely in the next upload.

---

### Post by VMC on 2010-11-12
The LiveCD now boots. Using todays second ISO release, which included the updated kernel-2.6.37-3.11 as Andy Whitcroft explains [_**here**_]("http://www.linux-archive.org/ubuntu-kernel-team/451735-linux-kernel-2-6-37-3-11-uploaded-abi-bump.html"). 

The AUFS is now fixed, but I'm stuck at the Plymouth logo section. The var logs show it has something to do with my nvidia section.

I'm going to mark this topic solved as the LiveCD now boots.

---

### Post by ranch hand on 2010-11-12
The only question I have is will they come to their senses and drop Plymouth for 11.10?

It would be nice to be able to boot Ubuntu without having to screw with a bunch of stuff just to get a boot that is slower than Debian.

Heck, I might even use Ubuntu as an OS rather than a FUN toy that is not reliable enough to use as an OS.

---

### Post by cariboo on 2010-11-12
In Mark's keynote speech at UDS-N he stated that there are plans to make plymouth work on all systems no matter what graphics adapter you use.

---

### Post by keypox on 2010-11-12
> **VMC said:**
> 

The AUFS is now fixed, but I'm stuck at the Plymouth logo section. The var logs show it has something to do with my nvidia section.



Yeah im stuck there too.   Not sure how a problem can be solved by another problem :mad:

---

### Post by VMC on 2010-11-13
> **keypox said:**
> Yeah im stuck there too.   Not sure how a problem can be solved by another problem :mad:

Apparently its not just nvidia related. I just tried it using the i386 ISO on a Radeon and it stops at the same place. 

I'm sure in a couple of days, some updates will come through that will progress it further. It is very early in the cycle. I'm just surprised , and glad that we have the ISO at all, at this stage. Now I can keep the ISO updated using zsync. :)

---

### Post by oboedad55 on 2010-11-13
Same here. Would someone please confirm I have the correct URL for the daily images? I have; [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Thanks!

---

### Post by floydsp on 2010-11-13
There is a 12.1 up there now am downloading it now..The reason I am wanting this one the alternate disc would not accept my password that I always use says to weak try again

Well still won't boot up for me just get the purple and blue screen

floydsp

---

