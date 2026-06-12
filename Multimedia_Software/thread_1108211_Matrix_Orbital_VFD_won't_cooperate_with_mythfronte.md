---
title: "Matrix Orbital VFD won't cooperate with mythfrontend"
date: 2009-03-27
forum: Multimedia Software
---

### Post by Big_Rog on 2009-03-27
I have a Matrix orbital VK202-24-USB VFD that works fine running LCDd and lcdproc by themselves, but mythfrontend fails to connect to the unit.  Attempting to either complete or back out of the "appearance" menu in the frontend itself causes the frontend GUI to hang.

Some things I've tinkered with so far:

[LIST][*]Change the listen port in LCDd.conf to 6545.  Mythfrontend.log was complaining about not being able to connect to mythlcdserver on that port.  No luck with that.  Changed lcdproc.conf to match so that I could verify that the unit was at least functional, which it still is.

[*]Scour the web for other people having similar issues.  There seem to be some people with an iMON VFD that have problems getting things working, but none seem to be related to my issue.

[*]Search the mythconverg database for references to "6545" with no luck as well.  I found the keys for the LCD settings (LCDEnable and the like) in the table data.  Strangely enough, the LCD shows on/"1" for hostname <mycomputer> but off/"0") hostname "ubuntu".
[/LIST]

I'm not even sure where else to begin tinkering to get this working.  I can post logs and configs if needed.  Thanks in advance!

 * UPDATE *

Well, somehow I've got LCDproc server acknowledging that mythlcdserver has connected.  LCDproc server screen shows 0 clients connected before starting mythfrontend, then shows 1 when mythfrontend starts.  Strangely the screens don't cycle through.  I have most of the LCD options checked in the frontend setup, but none of them show up on the VFD.

The on-screen menu hang issue seems to be related to some process that isn't cooperating behind the scenes.  I ran the frontend from the CLI with "-v important" and see that when the menus aren't responding to key presses  there are at least 5 attempts to restart the backend before the menu finally changes.

 * UPDATE *
Oh, I guess it would also help to have some info on my system.
  Mythbuntu 8.10 desktop 386 (2.6.27-11 generic)
  LCDproc 0.5.2
  Matrix Orbital VK202-24-USB pcb rev1.6

If this thread would be better served in the mythtv/mythbuntu threads, please feel free to relocate it.

---

