---
title: "M$ MCE USB IR Blaster + lirc + mythtv"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by Shr00mSter on 2007-01-11
Ive successfully setup Ubuntu (Edgy).  MythTV runs fine and I can control it with my Microsoft MCE [[COLOR="blue"]remote[/COLOR]]("http://www.newegg.com/Product/Product.asp?Item=N82E16880100851") ([COLOR="Red"]note the picture of the IR Blaster[/COLOR]).

So basicly all of my hardware is setup and working except the included dual IR Blaster for my digital cable boxes.  I know lirc says it supports the IR Blaster on the 'new' version of the remote I have but I can't find any documentation on how to get it working.

I'm figuring I need to get the ir codes for my cable boxes (Motorola DCT2244's), put the config file somewhere and tell lirc to send those signals to the IR blasters when myth requests the channel to be changed.

Has anyone seen a HowTo for this?  I've been searching the web all morning.

Thanks in advance.

---

### Post by pilesofspam on 2007-02-05
The DCT2244's and similar have a serial port- you can connect your MythTv machine to it directly.

Here's some code to run on channel change:

[http://mythtv.org/pipermail/mythtv-users/2003-October/016829.html](http://mythtv.org/pipermail/mythtv-users/2003-October/016829.html)

---

