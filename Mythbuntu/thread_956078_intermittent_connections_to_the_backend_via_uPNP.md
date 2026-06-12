---
title: "intermittent connections to the backend via uPNP"
date: 2008-10-22
forum: Mythbuntu
---

### Post by PA23 on 2008-10-22
first this is my first attempt at using mythtv I tried looking around for answer but never seemed to find anything that seemed to match my problem.

I just set up mythubuntu 8.04.1 desktop i386 as downloaded last night.  The system is a vanilla Intel P4 2Ghz machine using an Intel M/B (D845GBV) and a PVR-350 video card.  There are no other expansion cards installed.

There are two IDE hard disks, a 40GB and a 200GB the 200GB is mounted as /var/lib/mythtv and is an XFS filesystem.  The install CD was loaded on a USB CD-rom drive.

I am trying to connect via uPNP from two different devices, one a Buffalo linktheater PC-P3LWG/DVD and from an xbox running XBMC.  Everything seemed to be working great until earlier this afternoon.  I noticed the failure shortly after removing the USB CD rom drive from the system, I was no longer able to connect remotely to the Mythtv system.  I tried a reboot and still no success.  I then processed all the waiting updates and still to no avail.

The system is continuing to record shows.

occasionally the Mythtv backend will appear on the network, however when it does I may not see my recorded shows, or if the recorded shows don't appear I can exit the listing and re-enter the listing and the shows appear again.  If I try to start viewing a show it may start but will only run for a few minutes until it freezes, all the while I believe the backend continues to record.

I have also found that while using the mythweb interface I can view everything except the backend status.

looking through the logfiles in /var/log/mythtv I see the following whenever I try to access the backend:

2008-10-22 21:16:25.512 adding: mythtv as a client (events: 0)
2008-10-22 21:17:41.626 MainServer::HandleAnnounce Monitor
2008-10-22 21:17:41.629 adding: mythtv as a client (events: 0)
2008-10-22 21:17:45.260 MainServer::HandleAnnounce Monitor
2008-10-22 21:17:45.270 adding: mythtv as a client (events: 0)
2008-10-22 21:18:31.757 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-10-22 21:18:31.801 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-10-22 21:18:51.205 MainServer::HandleAnnounce Monitor
2008-10-22 21:18:51.219 adding: mythtv as a client (events: 0)

any suggestions would be greatly appreciated!

Thanks, Jeff

---

