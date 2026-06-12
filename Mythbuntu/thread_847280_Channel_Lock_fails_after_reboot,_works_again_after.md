---
title: "Channel Lock fails after reboot, works again after running backend setup?"
date: 2008-07-02
forum: Mythbuntu
---

### Post by granicus on 2008-07-02
I am having a strange issue with Mythbuntu 8.04, to which I just upgraded from 7.10.  I've been able to recreate this three times now.

Upon reboot and entry into MythTV fontend, if I try to watch live TV or schedule a recording then I get an error stating that channel lock cannot be obtained.  Live TV shows the correct EIT information for the current program, but the signal shows as 0% (L__).

However, if I completely exit the frontend, enter the backend setup from the desktop, exit immediately (don't have to do anything else in backend, simply enter and exit), run mythfilldatabase, then enter the frontend again I immediately get channel lock and have no problems watching or recording anything.  

The ability to channel lock seems to persist after going through those steps, as I rebooted the system last night (and went through the above steps) and left the frontend running and then tested again this morning before leaving for work.  I was still able to get channel lock 10 hours later.

This behavior leads me to believe that either something isn't getting completely loaded when the system reboots that is getting loaded when I open the backend setup, or there is an access/permissions issue that gets resolved once the backend setup is loaded (and I've been prompted for my password).

Does anyone have any suggestions on how to resolve this?

Thanks in advance.

---

### Post by bah1976 on 2008-07-02
Instead of running backend setup, just run mythfilldatabase from a terminal window.  That's probably what is making it work - not the backend setup.  I'm still drawing a blank on the cause, but try that troubleshooting step to isolate the "fix".

The password prompt is to allow the stop & start of mythbackend.  You won't need the password to run mythfilldatabase.

---

### Post by granicus on 2008-07-07
> **bah1976 said:**
> Instead of running backend setup, just run mythfilldatabase from a terminal window.  That's probably what is making it work - not the backend setup.  I'm still drawing a blank on the cause, but try that troubleshooting step to isolate the "fix".

The password prompt is to allow the stop & start of mythbackend.  You won't need the password to run mythfilldatabase.

After running tests, it is not mythfilldatabase that is "fixing" the issue.  Upon bootup, simply stopping and starting the backend resolves the issue so it seems more a startup issue with the backend.

---

### Post by granicus on 2008-07-13
It is a startup issue with the backend.  Either it is loading before another required module has loaded, or it is not fully loading for some reason.  Immediately upon bootup, if I manually run "mythtv-backend stop/start" from the terminal, everything works fine.

---

