---
title: "network HP printer"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by jrev on 2006-05-05
Hello all,:) 
I try to configure my HP PSC 1510 as network (all ubuntu's) printer on the printer server PC 
I found the printer address with command "hp-probe" which gave me the address :
ipp://hp:/usb/PSC_1500_series?serial=MY57TD12RY0498  HP PSC_1500_series
after installing the printer (admin/printing/new printer) I sent a text to print from the printing server PC 
then get the message printing 1 jobs 
then if I look to the general tab in the printer properties I got 
Printing: Unable to lookup host 'hp' - Host name lookup failure
Can you tell me where lies the fault ?

Thanks for your point of view

---

### Post by Iowan on 2006-05-05
[QUOTE=jrev]
Printing: Unable to lookup host 'hp' - Host name lookup failure
[/QUOTE]
DNS issue?  I'm not much help - but you might search for info on DNS and hosts.

---

### Post by DarkStarDeity on 2006-05-05
I would hazard a guess that the spaces in the "MY57TD12RY0498 HP PSC_1500_series" part of the name might be causing the problem, but that's all can offer.

---

### Post by jrev on 2006-05-05
Some more infos from the error-log : 
In /var/log/cups/error-log :
[05/May/2006:15:56:19 +0200] Started filter /usr/lib/cups/filter/pstops (PID 29863) for job 18.
I [05/May/2006:15:56:19 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 29864) for job 18.
I [05/May/2006:15:56:19 +0200] Started backend /usr/lib/cups/backend/ipp (PID 29865) for job 18.
E [05/May/2006:15:56:22 +0200] [Job 18] Unknown option "serial" with value "MY57TD12RY0498  HP PSC_1500_series"!

if I change serial with usb I got unknow option "usb"

so I cannot see any clue ...

---

### Post by RedBoot on 2006-05-06
I'm not clear about your post. On the server PC, you should install the printer (admin/printing/new printer) as a local printer. I've done that on mine, then printed a test page and it came out. For what it's worth, hp-probe reports:

> hp:/usb/DESKJET895?serialSG94H130DXFB HP DESKJET_895C

But I did NOT need to know this to get it to print. It has to be successfully setup as a local printer before it's networked and shared.

---

### Post by jrev on 2006-06-02
thanks Redboot !
you have to have it as local printer on the server I have made a tutorial on printer sharing on ubuntu (in french) if anybody wants to translate it ?:)

---

### Post by RedBoot on 2006-06-05
=D> Mui bien, jrev (español?)
Tutorials have helped me many times.

---

### Post by cypresstwist on 2006-06-09
[You'll find a tutorial for setting up a HP PSC 1510 here]("http://www.myl.ro/forum/index.php?showtopic=2529"). It's in Romanian but you can figure it out just by looking at the commands.

---

