---
title: "No internet at start up"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by andlinux on 2006-04-17
I have recently formatted my laptop and installed ubuntu again, the problem that I have now is that if ubuntu has started I can't connect to my router, I have to open that network properties program and deactivate my wireless card and then activate it back.

This is the first time that I have this problem, I used ubuntu in the past to and had never this problem.

What can I do to fix this ?

---

### Post by Titus A Duxass on 2006-04-17
Need a little more information first:

Is it an on-board wireless or a pcmcia?
Have you used ndiswrapper or did ubuntu recognise it?

---

### Post by andlinux on 2006-04-17
[QUOTE=Titus A Duxass]Need a little more information first:

Is it an on-board wireless or a pcmcia?
Have you used ndiswrapper or did ubuntu recognise it?[/QUOTE]
I have an onboard wireless in my laptop but I don't use that, so I use a pcmcia card (prism chip) and ubuntu detected it and it works like a charm ;)

I have never used programs like ndiswrapper.

---

### Post by andlinux on 2006-04-17
[QUOTE=andlinux]I have an onboard wireless in my laptop but I don't use that, so I use a pcmcia card (prism chip) and ubuntu detected it and it works like a charm ;)

I have never used programs like ndiswrapper.[/QUOTE]
Found the problem (I think ;)  ) It was because of an applet, wireless connection manager, I removed it and now the problem is also gone.

---

