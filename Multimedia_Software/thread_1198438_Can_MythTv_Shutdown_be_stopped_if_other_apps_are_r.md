---
title: "Can MythTv Shutdown be stopped if other apps are running?"
date: 2009-06-27
forum: Multimedia Software
---

### Post by gdbutcher on 2009-06-27
I'm running MythTV on Jaunty 9.04 64 bit. I've just added a shutdown command in MythTv to stop my PC running all night when a recording stops, but now MythTV shuts down unless there is a recording scheduled in the next 2 hours.

Can I get it to check if Transmission, Evolution, Firefox, or VLC are running? and only if "No" then to shutdown?

This guide [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake") In the **MythShutDownCHeck**  sections hints that it can be done but I can't find any further guidance or examples. Anyone point me in the right direction? 

My settings in Mythbackend setup:

Block shutdown before client connected: Unchecked
Idle shutdown timeout: 180
Max. wait for recording: 120
Startup before rec.: 0
Wakeup time format: hh mm
Command to set Wakeup Time:
Server halt command: sudo shutdown -h -P now
Pre Shutdown check-command: exit 0
 
This guide seems

---

