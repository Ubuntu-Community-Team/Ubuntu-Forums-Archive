---
title: "audacity snap cannot open files"
date: 2023-12-27
forum: Multimedia Software
---

### Post by hvieren on 2023-12-27
with audacity snap you get a huge confinement qua reachable files.
you can avoid this by downloading audacity appimage from

[https://www.audacityteam.org/download/linux/](https://www.audacityteam.org/download/linux/)

---

### Post by TheFu on 2023-12-28
All **snaps** have confinement constraints.  It is a "feature" according to the Snap designers and they don't provide any way around it if you don't place storage where they think you should.

**Flatpaks**, OTOH, have confinement, but with local controls. Also, flatpaks are meant to be used only for end-user, GUI programs, not server daemons.
**AppImages** are a single, bloated, file that contains all the dependencies.  There is good and bad with that. Sometimes the packager doesn't include all the required dependencies in every AppImage, especially if they are Qt or GTK+ libraries, which can be almost 1GB in size.

So, each has capabilities that others do not. Some are mandated, which can be excellent or terrible. Just depends on your needs.

I must say, that I use NFS storage and place it in specific locations outside where the snap team thinks it must go.
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D1                              nfs4  3.5T  3.5T   50G  99% /d/D1
istar:/d/D2                              nfs4  3.6T  3.6T   50G  99% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   25G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  3.2T  239G  94% /d/D6
istar:/d/D7                              nfs4  3.6T  956G  2.5T  28% /d/D7
```
None of that storage as mounted on the NFS server, nor on each client system, can be accessed by any Snap programs.  On some systems, even end-user HOME directories are placed on NFS and don't get mounted to /home/ .... which really freaks out the entire snap subsystem. Insisting that we relocate where HOME directories are placed is not a viable work-around. Our clients don't want to be forced to change their elegant NFS setup for 2K client users just for 1 OS with a poorly thought out constraint system.  They use /u/[a-z]/{username} system and only mount via autofs the specific, required, HOME directories to the clients based on who is actually logged in at the time.  This solution has worked for 25+ yrs across Unix and Linux systems, so asking them to change is unreasonable.

---

