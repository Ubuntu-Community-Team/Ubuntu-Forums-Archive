---
title: "Cannot connect to backend server reopened"
date: 2013-06-28
forum: Mythbuntu
---

### Post by ceesquared on 2013-06-28
I know that this is reopening an older thread but I think I have a good insight to this problem. I have a dual core CPU (could be very relevant) and a combined FE/BE and on auto start of Mythtv I get the dreaded "cannot connect to backend server. Here is a combination of my FE and BE logs from /var/log/mythtv/
Jun 26 15:37:17 MythTV mythbackend[1542] # starting the BE
Jun 26 15:37:17 MythTV mythbackend[1542]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.

Jun 26 15:37:19 MythTV mythfrontend[1873]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
 # this failed and gave the error message


Jun 26 15:37:29 MythTV mythbackend[1542]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6543

Note that the BE opened up port 6543 10 secs AFTER the FE tried to connect to it.

The immediate solution was to edit /usr/share/mythtv/mythfrontend.sh and insert after symlink - sleep 11
I think that this problem may be caused by the dual CPU loading two modules at the same time viz BE & FE. If any developers read this, then a possible solution is not to issue a PID until loading is complete. A check could then be made for a PID before trying to load the FE. Folks with quad core CPU may get even bigger problems!

---

