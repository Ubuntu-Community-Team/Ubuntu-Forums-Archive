---
title: "Epson DX8400 Scanner Driver trouble with Ubuntu 9.04"
date: 2009-04-26
forum: Multimedia Software
---

### Post by mo7ard on 2009-04-26
Hi!

I'm a recent linux user. Some months ago I installed Ubuntu 8.10, and got everything working sweet ;)...

After the recent Ubuntu 9.04 release, I download the new version and installed it... but I've got a situation that could use a hand from all you experts :-k... please!

I was able to install and configure my Epson DX8400 Scanner Driver with Ubuntu 8.10 with almost no trouble at all, but there's something going wrong now with this new release.

I went the same instruction path, but when I try to install the file **iscan_2.19.0-4_i386.deb** (the scanner driver from [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)), I get an error:
[IMG]http://img209.imageshack.us/img209/9017/errot.jpg[/IMG]
... if you find it difficult to translate the portuguese output error, please say so.

When I run the file, it checks for dependencies and says It's ready to intall. So I press the Install Now button, and just after a few seconds, it outputs what I posted above.

And so I ask you... Have I got to reinstall my old 8.10 to get my scanner working? :(

Thank you all! Best regards...


**mo[COLOR=DarkOrange]7[/COLOR]ard**

---

### Post by marcoworld on 2009-04-26
i have the same problem

---

### Post by ggerri on 2009-04-27
Hi there

just solved my problem in getting my GT-2500 running - after almost going nuts here ;-) :popcorn:

go to synaptic and install 

libsane-extras

restart

and you're done. :P

Hope that also solves your problem, even your model is not explicitly listed here:

[http://manpages.ubuntu.com/manpages/jaunty/man5/sane-epkowa.5.html](http://manpages.ubuntu.com/manpages/jaunty/man5/sane-epkowa.5.html) 

also check out [https://launchpad.net/ubuntu/jaunty/+source/sane-backends-extras/1.0.19.11ubuntu2](https://launchpad.net/ubuntu/jaunty/+source/sane-backends-extras/1.0.19.11ubuntu2)

AND:

For anybody who has a hard time in getting ubuntu seeing any scanner: check out your BIOS and ENABLE the "USB Device Legacy Support". This also solved my problem, that my Samsung Phone could not be found when connected via USB :guitar:

---

### Post by mo7ard on 2009-04-29
Thanks mate, but it didn't help in my case.

I have the last libsane-extras version installed (the one the link target to), but it still does't work... it must be something else... maybe an incompatibility in the new core?! :(

---

### Post by mo7ard on 2010-01-15
... installing libsane-extras actually worked! I was doing something wrong... it did solve my problem in getting the Epson DX8400 scanner driver working in Ubuntu 9.04.

---

