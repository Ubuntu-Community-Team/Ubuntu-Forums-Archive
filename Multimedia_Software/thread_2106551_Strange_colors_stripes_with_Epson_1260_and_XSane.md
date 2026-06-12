---
title: "Strange colors stripes with Epson 1260 and XSane"
date: 2013-01-19
forum: Multimedia Software
---

### Post by JRBASTIEN on 2013-01-19
XSane (or Sane) seems to be broken with Epson 1260 scanners.  It used to work perfectly fine but now I got large stripes of colors in the scan I make.  See sample here: [http://ubuntuone.com/5so901zHE0yFg4R0ANS3w3](http://ubuntuone.com/5so901zHE0yFg4R0ANS3w3)

No problem on first scan (or preview) then I get these stripes in subsequent scans. The only workaround is to shutdown XSANE and to restart it. And of course, never use the preview function.

Perhaps it is the first time I tried since I upgraded to Ubuntu 12.04 64 bits. Previously I was on 10.10 32 bits.

Many people reported the issue but none of those threads got resolved:

[http://ubuntuforums.org/showthread.php?t=12462594](http://ubuntuforums.org/showthread.php?t=12462594)
[http://ubuntuforums.org/showthread.php?t=1472373](http://ubuntuforums.org/showthread.php?t=1472373)

Does anybody have this issue and knows how to resolve this?

---

### Post by JRBASTIEN on 2013-01-20
I'm talking to myself here hoping someone can help me out.  In the Xsane official site ([here]("http://www.xsane.org/")), it says:

*If you experience any problems with XSane and sane-backends with a version number greater than 1.0.19 then this may be caused by an incompatible development of sane-backends. In this case it may be worth to try sane-backends-1.0.19 or earlier*

On 12.04, libsane is 1.0.22-7ubuntu1.  How can I roll it back to 1.0.19?

---

### Post by pdc on 2013-01-22
I am wondering which drivers you are using; and if you using the Epson drivers would help?

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

looks like [COLOR="SeaGreen"]iscan_2.10.0-1.tar.gz[/COLOR] 

and the plug-in is an rpm ([COLOR="SeaGreen"]iscan-plugin-gt-7300-1.0.0-1.c2.i386.rpm[/COLOR])

so could be installed with [COLOR="Blue"]alien[/COLOR]

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

> [COLOR="Red"]sudo apt-get install alien[/COLOR]

and then

> [COLOR="Red"]sudo alien -i iscan-plugin-gt-7300-1.0.0-1.c2.i386.rpm[/COLOR]


64bit systems always sound much more impressive than 32bit; with older pieces of hardware, some find a working 32bit better than a troublesome 64bit

---

