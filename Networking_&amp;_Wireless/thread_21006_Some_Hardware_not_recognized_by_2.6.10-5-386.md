---
title: "Some Hardware not recognized by 2.6.10-5-386"
date: 2005-03-19
forum: Networking &amp; Wireless
---

### Post by markdone on 2005-03-19
I installed the new 2.6.10-5-386 kernel and my network card, wireless card, and external keyboard and mouse (I have a laptop) are all not recognized in it.  They are all recognized and work under 2.6.10-4-386 kernel.  Any suggestions besides keep using the old kernel?  Thanks for the help.

---

### Post by BaffledMollusc on 2005-03-19
[QUOTE=markdone]I installed the new 2.6.10-5-386 kernel and my network card, wireless card, and external keyboard and mouse (I have a laptop) are all not recognized in it.  They are all recognized and work under 2.6.10-4-386 kernel.  Any suggestions besides keep using the old kernel?  Thanks for the help.[/QUOTE]

What sort of laptop is it?

Regarding the wireless card, maybe you could use ndiswrapper? This is an application that wraps windows drivers so they work under linux, so if your network card is supported under windows you should be okay. There are lots of posts about it and probably a howto somewhere, but one thread is [http://ubuntuforums.org/showthread.php?t=20298](http://ubuntuforums.org/showthread.php?t=20298).

---

### Post by markdone on 2005-03-20
The laptop is a Toshiba Satellite A35-S1592.

---

### Post by az on 2005-03-20
I am running on a toshipa satelite pro 460

Is this bug relevant?  If so, add comments...
[http://bugzilla.ubuntu.com/show_bug.cgi?id=6566](http://bugzilla.ubuntu.com/show_bug.cgi?id=6566)

---

