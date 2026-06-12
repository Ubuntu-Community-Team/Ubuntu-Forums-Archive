---
title: "NX 4 Preview 6 on 12.04 - Gnome session not available"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by jayage on 2012-11-13
I've installed Nomachine 4 Preview 6 on 12.04 to get access to the new Web Player. It sort of works - I can connect to the server, but only using shadow session. No other is available, although gnome should be.

It used to work using version 3.5, but no dice on version 4.

Here's what I get when querying for available sessions:

```
$ sudo /usr/NX/bin/nxserver --resourcelist --class session
NX> 104 Resource list:

Class     Type                       Value
-------   -----------------------    ------
session    unix-kde                  no    
session    unix-default              no    
session    shadow                    yes   
session    shadow-windows            no    
session    unix-xdm                  no    
session    windows                   no    
session    shadow-mac                no    
session    unix-gnome                no    
session    unix-cde                  no    
session    unix-application          no    
session    unix-desktop              no    
session    unix-console              no    
session    vnc                       no    
session    unix-script               no    
NX> 999 Bye.
```Google searches turned up nothing usefull. Anyone has the same problem, or even better had it and figured it out?

I'd hate to go back to 3.5, but right now it looks like it...

---

### Post by QIII on 2012-11-13
I never could get 4.0 to work well.  It's also only a trial version and the trial period is not long.

I'd just stick with 3.5.

Supposedly USB forwarding will be available in 4.0, which would be nice.  Audio may actually work right, too.

---

### Post by mcasperson on 2012-12-11
I have found the same problem. No matter what I specify in the AvailableSessionTypes in server.cfg, the shadow session is the only resource that is actually available. Which is not great since I have a headless server and nothing to shadow.

---

### Post by rjshera on 2013-01-05
I had the same problem until I installed the "Nomachine Virtual Desktop Workstation for Linux" which is available in the "NoMachine for the Enterprise" download group.

Once I installed this I had no problem; the option to start a new virtual session appeared one I connected.  I think this is one of the key differences between NX3.5 and NX4.  The free version of NX4 appears to only support shadowing of a local console session, and doesn't support virtual sessions.

---

### Post by jayage on 2013-01-09
> **rjshera said:**
> I had the same problem until I installed the "Nomachine Virtual Desktop Workstation for Linux" which is available in the "NoMachine for the Enterprise" download group.

Once I installed this I had no problem; the option to start a new virtual session appeared one I connected.  I think this is one of the key differences between NX3.5 and NX4.  The free version of NX4 appears to only support shadowing of a local console session, and doesn't support virtual sessions.

Thanks for the hint, rjshera!

Looking at the descriptions of the NX4 packages now, it would've been prudent to actually read them before downloading.

You've been a big help. 

Cheers,
Jay

---

### Post by Narog82 on 2013-01-28
> **rjshera said:**
>  The free version of NX4 appears to only support ....

Rjshera you mention a free NX4 version, is this available or it will be after release?

---

