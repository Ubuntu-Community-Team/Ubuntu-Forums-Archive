---
title: "ksoftirqd consumes 100% CPU for several minutes"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by MSPdwalt on 2010-07-12
Hey guys,

I've had this problem recently.   Whenever I open an open office.org document from a cifs/SAMBA share as I navigate through it my laptop will lock up, and by lock up I mean so bad that I can't even move the mouse.  If I let it sit for anywhere from 30 seconds to 2 minutes it will come out of it.  Trying to navigate through the document again will trigger a similar episode.

I finally got fed up and opened a terminal with top and set it to always on top, then I opened my samba share, opened my spreadsheet. and proceeded to trigger my problem.  When the lockup happened it was so bad and so quick that top stopped updating and I wasn't even able to see something creep up in CPU usage.  As it came out of it top started updating in bursts, first ksoftirqd/0 was at 100%, then that dropped to near nothing, then xorg spiked to 100%, then the system returned to normal.

I googled around an found lots of speculation, and bug reports that were way above my head.  Some of the speculation suggested it was a kernel issue, but that has supposedly been fixed.  Another forum post said that it was a multi-processor issue. (the guy was running it in a vm so he just removed the vCPU) And yet another suggested a network issue/attack.

I am not well versed in troubleshooting these types of issues in Linux so any advise would be greatly appreciated.

I am running a Dell Latitude D620 with a dual core Intel proc and a Broadcomm network card (wired) and an Intel wireless card.  I have all the latest updates.  The shares I experience this issue with (only shares I really use) are on a Netapp and are active directory integrated (my laptop is not joined to the domain)

Any suggestions would be greatly appreciated,

DW

---

### Post by MSPdwalt on 2010-07-26
Disabled anti-aliasing in Open Office

---

