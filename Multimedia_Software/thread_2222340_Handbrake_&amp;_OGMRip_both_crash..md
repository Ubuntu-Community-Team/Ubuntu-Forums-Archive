---
title: "Handbrake &amp; OGMRip both crash."
date: 2014-05-06
forum: Multimedia Software
---

### Post by Christopher_Clark on 2014-05-06
Hello Everyone,

I have a bit of a weird problem here I'm currently using Ubuntu 14.04 both Handbrake & OGMRip crash shortly after starting an encode, movie makes no difference.
I always create an ISO of the DVD in question before starting an encode, All ISO's play fine. This computer is a recent build and I have not been able to 
successfully encode anything on it as of yet.

Any help would be greatly appreciated ...

AMD FX(tm)-8350 Eight-Core Processor × 8
16GB DDR3 Corsair RAM
Samsung 500GB SSD

If you need more information please let me know.
Thanks in advance..

---

### Post by SeijiSensei on 2014-05-06
What version of Handbrake are you using?  I found the 14.04 version in Stebbins handbrake-snapshots PPA rather unstable, so I ended up [using the version for Raring in handbrake-releases]("http://ubuntuforums.org/showthread.php?t=2221790&p=13013059&viewfull=1#post13013059").  That worked fine for me just the other day on Kubuntu 14.04.

---

### Post by Christopher_Clark on 2014-05-06
I have tried handbrake-releases PPA, handbrake-snapshots PPA, the version that's actually in the the ubuntu repos now, and have compiled it from source.
I have also tried several other similar programs all with very similar results (encoding begins but will not get very far, less than 20% or so).
Thought it may be a hardware problem but I have tested everything (CPU, Memory, HD, etc). I'm a technician and this system is a recent build.
The computer has no other problems and functions perfectly aside from actually completing an encode.

Full specs can be provided.

Thanks in advance ...

---

### Post by SeijiSensei on 2014-05-06
Do you see anything in /var/log/syslog when the encoding slows down?  

Can you write the output to a network location rather than the hard drive?  What if you encode from a DVD ISO rather than the disc itself?  I'm trying to think of ways to avoid using one or another piece of hardware.  The most isolation would be putting the ISO on a ramdisk and writing the output there as well, or writing the output over the network to a server.

---

### Post by Christopher_Clark on 2014-05-06
I always use an ISO of the DVD for the encoding. I have tried reading from and writing to different HD's internal and external, nothing shows up in syslog, and the crash only says segfault. I recently tried encoding using various different settings, and managed to get it to go much furthur but it still fails, sometimes the program will just lock up, sometimes the encode will just stall forever, and sometimes it locks up the whole system. Ran a test on the memory (no problems). Also I've been keeping an eye on the CPU temp nothing out of the norm there either.

Thanks for any help ...

---

### Post by Christopher_Clark on 2014-05-06
This is a standard install of Ubuntu 14.04 (64bit) with standard kernel fully up to date, I can give software versions and full hardware specs if needed..
Thanks again ...

---

