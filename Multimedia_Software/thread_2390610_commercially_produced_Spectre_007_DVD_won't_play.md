---
title: "commercially produced Spectre 007 DVD won't play"
date: 2018-04-30
forum: Multimedia Software
---

### Post by Spaceman9 on 2018-04-30
The commercially produced Spectre 007 DVD and a commercially produced Detective Montalbano DVD will not play in my install of Ubuntu 17.10.01. Other DVDs play without any problems. I suppose I need a codec for the two aforementioned DVDs. What do I need to install? Thanks for any help.

---

### Post by oldos2er on 2018-04-30
You probably need libdvdcss2,  see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Spaceman9 on 2018-04-30
Hi oldos2er. I tried installing that and I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvd-pkg is already the newest version (1.4.0-1-2).


So, that's already installed.

---

### Post by Autodave on 2018-04-30
I have several newer DVDs here that will not play on any PC: Mac, Linux, or Windows 7 & 10.  They play just fine in a DVD player though. From what I understand, they are now putting "bad" blocks at the beginning of the DVD. A PC goes crazy and cannot read them, so it stops. Your DVD player though just ignores them and goes until it finds a block that it can read.

---

### Post by Spaceman9 on 2018-04-30
Hi Autodave.

I've never heard of that before. Funny thing is when I had Ubuntu 16.04 LTS installed I could play the Detective Montalbano DVD. BTY these DVDs won't play in my install of Windows 7 either. I've heard Linux Mint will play anything though. I don't know.

---

### Post by tinylagarto on 2018-05-07
I would give it a last try with regionset.

[http://manpages.ubuntu.com/manpages/bionic/man8/regionset.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/regionset.8.html)

---

