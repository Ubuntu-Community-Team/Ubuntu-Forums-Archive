---
title: "alsaconf script is here!!"
date: 2006-04-08
forum: Multimedia &amp; Video
---

### Post by FarEast on 2006-04-08
There are a lot of people who have problems in configuring ISA sound cards, I put a script called 'alsaconf' here.
[ATTACH]8103[/ATTACH]
Usage:
$ gunzip -v alsaconf.gz
$ chmod 755 alsaconf
$ sudo ./alsaconf

Note:
You may need to install the package 'libncurses5' to run it.

---

### Post by FarEast on 2006-05-04
Hi;) ,
It seems there are quite a few guys who are having problem in getting their sound cards to work.  It may be faster to try this *wizard*(alsaconf).

If your trial is a success, please report on:
1) type of the sound chip
2) contents of /etc/modprobe.d/sound written by the script

One more remark:
In my experience, old fashioned sound chip do not seem to be capable of playing back sound files made with high sampling rate.  So you will be able to hear only system sound with low sampling rate even if you have succeeded in configuring it.  I recommend to buy a cheap USB sound devices rather than struggling.

:p

---

