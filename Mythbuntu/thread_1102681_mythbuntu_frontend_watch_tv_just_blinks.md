---
title: "mythbuntu frontend watch tv just blinks"
date: 2009-03-21
forum: Mythbuntu
---

### Post by jbkott on 2009-03-21
Cant get Mythbuntu frontend "Watch TV" function to work. This does work on the frontend/backend in my basement without problems.

My frontend can connect to the database and I think I have all needed directories connected via NFS with the needed permissions (can write/read to all).

When I select "Watch TV" on the frontend the screen flashes black for a second and returns to the main menu.

Running mythfrontend -v playback and selecting "Watch TV" indicates the following. I tried to trim the output to pertinent info.



2009-03-21 22:29:15.003 Connecting to backend server: 192.168.1.7:6543 (try 1 of 5)
2009-03-21 22:29:15.004 Using protocol version 40
2009-03-21 22:29:15.016 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 22:29:15.016 RemoteEncoder::openControlSocket(): Connection timed out.
2009-03-21 22:29:15.018 GetEntryAt(-1) failed.
2009-03-21 22:29:15.020 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2009-03-21 22:29:15.020 TV Error: LiveTV not successfully started
2009-03-21 22:29:15.020 TV Error: LiveTV not successfully started
2009-03-21 22:29:15.022 TV: Deleting TV Chain in destructor
2009-03-21 22:29:15.030 DPMS Deactivated 
2009-03-21 22:29:15.034 DPMS Reactivated.

I looked through my backend logs and didn't find much. Only line that looks like it might apply is below...

2009-03-21 22:23:00.882 MythSocket(9ca8418:-1): writeStringList: Error, called with unconnected socket.

I am at a loss. If anyone can I help I would really appreciate it. Thanks!!

---

