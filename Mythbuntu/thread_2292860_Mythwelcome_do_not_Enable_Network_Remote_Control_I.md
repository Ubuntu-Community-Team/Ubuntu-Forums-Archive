---
title: "Mythwelcome do not Enable Network Remote Control Interface"
date: 2015-08-31
forum: Mythbuntu
---

### Post by 4ps4all on 2015-08-31
Mythbuntu 14.04.02
0.27.5+fixes.20150803.e2a11c9-0ubuntu0mythbuntu3

I'm using mythwelcome in a mythtv backend and frontend DVR-system.
To shutdown the computer I have to close MythtvFrontend, so that mythwelcome can make all the necessary checks before to shutdown the DVR-system.
I use as remote “mythmote app” on android to control MythTvFrontend, but it works only when MythTvFronted is active.

So if I close MythtvFrontend , my remote is not anymore working with MythWelcome.
I suppose MythWelcome should let me use my “mythmote app” remote, otherwise I can't start MythtvFrontend from "mythmote app" remote, neither I can lock the shutdown if necessary.
Am I right? 


While MythtvFrontend is running
telnet 127.0.0.1 6546 
Trying 127.0.0.1... 
Connected to 127.0.0.1. 
Escape character is '^]'. 
MythFrontend Network Control 
Type 'help' for usage information 


If I close MythtvFrontend, and mythwelcome is running
telnet 127.0.0.1 6546 
Trying 127.0.0.1... 
telnet: Unable to connect to remote host: Connection refused

and naturallly “mythmote app” is not working anymore.

---

