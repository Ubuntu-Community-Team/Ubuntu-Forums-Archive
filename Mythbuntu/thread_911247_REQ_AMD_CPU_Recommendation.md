---
title: "REQ: AMD CPU Recommendation"
date: 2008-09-05
forum: Mythbuntu
---

### Post by frego on 2008-09-05
I have an Asus A8N-E motherboard which currently has a AMD64 3800+ cpu in it.  I would like to upgrade this to a faster cpu.  This is a slot 939 board, compatible with the Athlon 64, the Athlon 64 X2, and the Athlon 64 FX.  I currently have the 64 bit version of Mythbuntu 8.04 on this machine and would like to not have to reinstall.  First, which is the best chip for me?  Second, what would I have to do to get the SMP kernel? 

PS:  I use this machine for my myth backend and frontend as well as my VMWare server, Azureus, etc.  It is currently maxed out on RAM at 4GB.

---

### Post by tuxxy on 2008-09-05
Depends what your price range is like, the AMD X2 are great chips

---

### Post by newlinux on 2008-09-05
I have the same mobo with and AMD X2 3800 and 2GB PC3200. The generic kernel in ubuntu is SMP enabled, and most likely you are already using and SMP kernel (you just don't have 2 cores/CPUS to  use). MOBO has been solid for me. 

```

uname -a

```
should tell you your kernel and SMP status I believe.


It's hard to know what you'll need because you haven't specified how it is doing for you now with the single core or how much more power you'll want, or what your criteria for "best" is (value, speed, etc.). A mythbackend doesn't take much CPU power unless it is doing a lot of transcoding and commercial flagging. Your current proc can decode MPEG-2 HD LiveTV and recordings. Where'd you'd need more from a multimedia standpoint is decoding 1080i/p h.264 or VC-1. Any dual core can handle reasonably easy most other formats. On mine I play back HD MPEG-2 all the time and can do 720P x.264. It is also a mythbackend, and a freenx server and the processor is rarely taxed.

---

### Post by frego on 2008-09-05
Thanks for the input guys!  It looks like my kernel is SMP enabled.  My load average has been quite reasonable when using myth.  I currently watch HD once in a while in MythVideo, but not through the TV tuner.  I do transcode and commercial flag.  I think VMWare and Azureus are bigger loads on this box.  I was thinking an X2 chip might be nice because of the VMWare server running on here where I run an XP desktop and sometimes another image or two and connect to it via a different machine.  I also plan on setting up more DVD ripping jobs and cluster this with my Ubuntu desktop using DVD::rip at some point in the future.  So I guess I'd like to throw the max CPU I can at it.  But I know this MB is limited as it is a socket 939 which I understand are now obsolete.  It says it has 2000/1600 MT/s HyperTransport bus.  Does that mean I can't use the Toledo cores?  I know this question is diverging from Mythbuntu, but does anyone happen to know what the max CPU is I can throw in here?

---

### Post by newlinux on 2008-09-05
Pretty sure you can use toledo cores.


The official compatibility list:
[http://support.asus.com/cpusupport/cpusupport.aspx?SLanguage=en-us&model=A8N-E](http://support.asus.com/cpusupport/cpusupport.aspx?SLanguage=en-us&model=A8N-E)
[http://www.cpu-upgrade.com/mb-ASUS/A8N-E.html](http://www.cpu-upgrade.com/mb-ASUS/A8N-E.html)


I used to run azareus 24/7 and it can be a hog, and VirtualBox with XP. I run ktorrent now, and it is a bit less of a hog, but still a hog sometimes none-the-less. I think the 939s  cost more than the AM2s unfortunately for some reason.

---

