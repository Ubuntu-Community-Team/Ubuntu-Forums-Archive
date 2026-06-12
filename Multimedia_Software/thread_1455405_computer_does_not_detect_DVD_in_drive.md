---
title: "computer does not detect DVD in drive"
date: 2010-04-15
forum: Multimedia Software
---

### Post by socref on 2010-04-15
Hello, everyone. Trying to help daughter with v 9.04.

I installed 9.04 on both two computers -- on an old PIII 667 box and on a dual core Intel (Dell).

DVDs play on the old PIII (jerky to be sure, but it's an old box with only 512 MB memory).

But the dual-core Intel does not even recognize that there is a DVD in the drive, so nothing happens after the disk is inserted and the drive activity light stops flashing. Nothing.

When we look in "Places" to see what drives appear on the Dell the hard drive icon shows up as does the optical drive icon. But clicking on that optical drive icon brings up a message that there is no media in the drive.

On the other hand, on the old PIII the DVD shows up in "Places" along side the hard drive and optical drive icons. Clicking on the DVD icon launches Movie Player (Totem) and the DVD plays.

I don't even know where to begin trouble-shooting this one so that the dual-core Dell will recognize that there is a disk in the drive and then play DVDs. 

We do have libdvdcss2 on both computers. 

One other item worth noting... Previously the Dell had SuSE Linux 11.1, and it did play DVDs without problem.

Is there an output file from the non-responding computer I can post to this list that would help identify what's preventing a DVD from being seen?

Thanks!
socref

---

### Post by yrhen on 2010-04-16
seems I am not the only one with dvd-drive problems.
I found a bug report [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806)
but it will take me a while to decipher whether or not it is related... I'm not half as clever as the ones writing those reports

---

### Post by socref on 2010-04-16
> **yrhen said:**
> seems I am not the only one with dvd-drive problems.
I found a bug report [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/397806)
but it will take me a while to decipher whether or not it is related... I'm not half as clever as the ones writing those reports

The link you posted does not work. Seems to be missing some characters in the middle. Can you repost complete link?
Thx
socref

---

### Post by yrhen on 2010-04-16
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806)

it is in the thread by ewaynec five postings up as well: though it seems more write related than read related, I'm afraid

---

### Post by socref on 2010-04-16
> **yrhen said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397806)

it is in the thread by ewaynec five postings up as well: though it seems more write related than read related, I'm afraid

Thanks. Yes, all of those posts seem related to newer versions of Ubuntu and to write problems. 

Anyone have any idea how to trouble shoot my problem of the DVD (movie) not being recognized as in the drive by Ubuntu 9.04?

Thx

---

### Post by yrhen on 2010-04-16
not a clue, 
but did you check ubuntugeek?
it is not my cup of tea, but has something to say about  libdvdcss2.

---

### Post by socref on 2010-04-21
Any thoughts on why the DVD drive does not recognize a DVD in the drive, yet it does recognize when CDs are in the drive?

Thx
socref

---

### Post by socref on 2010-04-30
Anyone? Thoughts on why drive does not detect DVDs but does see CDs? Yes, it is a DVD drive.  :P

Thx
socref

---

### Post by tanics on 2011-03-06
I have faced the same problem - and with same configuration -intel core2 duo - ubuntu 9.04 and I can't remember whether I have previously played DVD here or not.

1) **_Though the system face no problem in detecting Fedora 13 dvd (dvr-r)._**
2) It can't also detect blank dvd-r.
3) There is no problem in detecting, playing, writing CD's though.

Could it be a hardware problem?

---

### Post by MepisReign on 2011-03-06
Would you try to play a known-good disc on both?
Is the disc that your are trying to play scratched even a little?

It had happened to me in the past that the media is the problem, please go ahead and try another disc

MepisReign

---

### Post by tanics on 2011-03-06
I have just tried playing a newly bought DVD - after failing to do so I have googled and posted here.
After failing to play the DVD and some blank DVD too I have tried the Fedora 13 dvd and it recognize and mount the dvd instantly.
[U]Few months before I collect a dvd of windows 7 copy and try to install it in VBox but the experience is the same. So I made a copy of that Win7 dvd and then tried again - after failing I googled and use a command "sudo mount -t udf /dev/dvd1 /mnt" - and the win7 dvd gets detected and mounted.
[/U]
But that have not worked in this case and when I try to write a blank dvd.

---

