---
title: "HDHomerun Dual - LiveTV tuner problems"
date: 2015-01-13
forum: Mythbuntu
---

### Post by mbert on 2015-01-13
I am working towards getting rid of my cable service and replacing it with a MythTV setup using a HDHomerun Dual (HDHR4-2US) for OTA.

My current test setup is 1 Mythbuntu installation running as a VM on ESXi 5.5 for Myth backend, and 2 Mythbuntu bare metal installations (old pc's) running Myth Frontend.  I followed the instructions here ([https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual#MythTV_Setup](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Dual#MythTV_Setup)) for setting up the HDHomerun and have an active Schedules direct subscription.

Watching on one frontend works as expected, however if I try and watch on the second frontend I was unable to change channels.  Looking at the HDHomerun Config CUI shows that only one tuner is active as does MythTV backend status.  If I set two recordings via the web interface, both tuners from the HDHomerun are used.  I deleted the tuners, and recreated them to no avail.  The logs on the backend and frontend did not reveal anything (at least to me).  Pressing Y, while watching on a frontend does nothing, pressing C does show the current tuners label.

I was about ready to nuke everything and start over, when I discovered that if I open the guide and then select another channel the viewer seems to reopen and then uses the other tuner.  After this I am then able to change to two frontend channels freely, at least until I close one of the viewers.  If I open it back up again, I am back in the same position.   

So while I do have a work around, it would be nice to figure out why the tuners won't work without this, or why pressing Y won't allow changing tuners.

---

