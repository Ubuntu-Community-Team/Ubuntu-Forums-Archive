---
title: "Combo FE/BE - mythwelcome/mythshutdown - works manually, fails at countdown"
date: 2015-07-03
forum: Mythbuntu
---

### Post by MrBackhand on 2015-07-03
I am running mythbuntu 14.04 with all of the latest patches. I have read the following sets of instructions: [https://www.mythtv.org/wiki/ACPI_Wakeup](https://www.mythtv.org/wiki/ACPI_Wakeup) and [http://gedakc.users.sourceforge.net/display-doc.php?name=pvr-mythtv-auto-wakeup](http://gedakc.users.sourceforge.net/display-doc.php?name=pvr-mythtv-auto-wakeup) and [https://www.mythtv.org/wiki/Mythwelcome](https://www.mythtv.org/wiki/Mythwelcome) 

My motherboard uses UTC not in local time. I can manually echo + 5 mins to the rtc and pm-suspend mythtv and in 5 mins it boots back up and the backend starts and it works. mythwelcome/mythshutdown successfully adds a date/time to rtc to be awakened, but it fails to shutdown. It looks like it shuts down mythbackend but does not shutdown the machine or mythfrontend. I try to run commands after the failure and the backend is not up and i have to manually start it. I am not prompted for a password for the sudo commands when I run them manually.


```
Jul  3 12:55:42 mythtv mythbackend: mythbackend[2464]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: mythtv as a client (events: 1)Jul  3 12:55:43 mythtv mythbackend: mythbackend[2464]: I Scheduler scheduler.cpp:2883 (CheckShutdownServer) CheckShutdownServer returned - OK to shutdown
Jul  3 12:55:43 mythtv mythbackend: mythbackend[2464]: N Scheduler scheduler.cpp:2978 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011#011#011sudo mythshutdown --setwakeup 2015-07-03T18:51:40
Jul  3 12:55:43 mythtv mythbackend: mythbackend[2464]: N Scheduler scheduler.cpp:3009 (ShutdownServer) Running the command to shutdown this computer :-#012#011#011#011#011#011#011sudo mythshutdown --shutdown
Jul  3 12:55:44 mythtv mythbackend: mythbackend[2464]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID 1, UID 0, Value 0x00000000
Jul  3 12:55:44 mythtv mythbackend: mythbackend[2464]: N CoreContext main_helpers.cpp:706 (run_backend) MythBackend exiting
Jul  3 12:55:44 mythtv mythbackend: mythbackend[2464]: E Scheduler scheduler.cpp:3018 (ShutdownServer) ServerHaltCommand failed, shutdown aborted



```

Anyone had success or have suggestions?

Thanks!

---

### Post by blm-ubunet on 2015-07-03
The mythbackend runs as user "mythtv".

You have edited (only with sudo visudo) the "/etc/sudoers" file to allow user "mythtv" to run /sbin/shutdown, /usr/bin/setwakeup.sh.

You should triple check these files are in those locations..& the execute permissions on the script.
which shutdown
which setwakeup.sh

If you mess up the "/etc/sudoers" file with a normal editor then have to use "pkexec visudo" etc.

---

### Post by philip7 on 2015-07-24
> **MrBackhand said:**
> It looks like it shuts down mythbackend but does not shutdown the machine or mythfrontend.

For my setup I have to shutdown mythfrontend manually before the machine shutsdown, when I exit Mythfrontend I see the Mythwelcome screen with the countdown to shutdown.

Also what are your settings within Mythtv setup and Mythwelcome?

---

