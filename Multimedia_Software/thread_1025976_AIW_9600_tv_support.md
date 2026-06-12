---
title: "AIW 9600 tv support?"
date: 2008-12-30
forum: Multimedia Software
---

### Post by daddy4count on 2008-12-30
I found this post on the subject:

[http://ubuntuforums.org/showthread.php?t=907873](http://ubuntuforums.org/showthread.php?t=907873)

I just installed gatos, no problem.  But now I am getting this error when trying to run xatitv:

kidbox@kidbox-desktop:~$ xatitv
GATOS: No ATI PCI/AGP Cards ?
GATOS: gatos_inita(): Invalid argument
xatitv: gatos_init(): Invalid argument
kidbox@kidbox-desktop:~$ 

I have the FGLRX driver installed from ATI... tried "sudo aticonfig --initial" which seemed to work but still getting the "No ATI cards" error message.

I tried gatos-conf but it was no help...

My sysytem:
P4 3.0 GHZ x86
1GB RAM
ATI AIW 9600 Pro (AGP)

Ubuntu 8.10 "Intrepid" installed today!  


Are there arguments that I can pass to xatitv or a way to get gatos to recognize my video card?

I tried getting mythTV to work but it was a bust... thought I would give this a try.  So far no luck here either.

Thanks

---

