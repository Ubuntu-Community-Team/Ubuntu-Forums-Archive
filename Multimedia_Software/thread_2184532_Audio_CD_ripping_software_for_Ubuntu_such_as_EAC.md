---
title: "Audio CD ripping software for Ubuntu such as EAC"
date: 2013-10-29
forum: Multimedia Software
---

### Post by trulynon on 2013-10-29
Hello,

I am looking for similar software to EAC (Windows) for ripping Audio CD on Ubuntu 13.10. I am looking for a software with ability to create a log file with peak levels of the ripping tracks. Any help, please? Thanks

---

### Post by trulynon on 2013-10-29
Found it. Seems like [Morituri]("http://thomas.apestaart.org/morituri/trac/") does the job!

---

### Post by speartip on 2013-10-30
You might want to give Rubyripper a look. You can add the ppa from here:
[https://launchpad.net/~brandonsnider/+archive/ruby-ripper](https://launchpad.net/~brandonsnider/+archive/ruby-ripper)
IMO, the best linux ripper there is.
Untick  "create cuesheet" though it speeds up the rip significantly.

---

### Post by ebozzz on 2013-12-15
> **speartip said:**
> You might want to give Rubyripper a look. You can add the ppa from here:
[https://launchpad.net/~brandonsnider/+archive/ruby-ripper](https://launchpad.net/~brandonsnider/+archive/ruby-ripper)
IMO, the best linux ripper there is.
Untick  "create cuesheet" though it speeds up the rip significantly.

Ruby might not be a good option any longer. Looks like the developer is not as active. 

> :~$ sudo add-apt-repository ppa:brandonsnider/ruby-ripper
You are about to add the following PPA to your system:
 RubyRipper for those interested in using it.

Development has slowed down considerably at the time I'm writing this. The best current way to rip audio is Morituri, which is available in Precise and beyond.

The packaging here is based on Scott Leggett's latest packaging scripts for Debian.
 More info: [https://launchpad.net/~brandonsnider/+archive/ruby-ripper](https://launchpad.net/~brandonsnider/+archive/ruby-ripper)
Press [ENTER] to continue or ctrl-c to cancel adding it

---

### Post by shantiq on 2013-12-16
see below

---

### Post by shantiq on 2013-12-16
well rubyripper is fine there is a [version 7 in the works]("http://ubuntuforums.org/showthread.php?t=1533534&p=12757438#post12757438") and can be tried  otherwise [6.2]("http://ubuntuforums.org/showthread.php?t=1533534&p=12856457#post12856457") [ ]("http://linuxappfinder.com/package/rubyripper") still perfect


[EAC]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385") works also perfectly under Wine

---

