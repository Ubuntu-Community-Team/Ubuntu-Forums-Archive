---
title: "nVidia GeForce4ti &amp; Sony G400 refresh rate problem?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by handy on 2006-08-27
I just built up another machine out of odd bit's & pieces I had laying around.

Installed Dapper & Automatix, proprietary nVidia drivers, setup NFS network.  All good! :) 

Only real problem I have, is that when I edit the xorg.conf file, putting in the correct refresh rates for my monitor, X fails at reboot!?? :confused: 

I have tried multiple times, leaving the max' res' at 1024x768...

I know the GeForce4ti can handle it, I've used it in the past for years with the same monitor & windoze...

Got me stumped, any assistance appreciated, thanks... :KS

---

### Post by croak77 on 2006-08-28
Did you put in the right VertSync and HorzSync? As well asa make sure you are loading nvidia and not nv?

---

### Post by handy on 2006-08-28
> **croak77 said:**
> Did you put in the right VertSync and HorzSync? As well asa make sure you are loading nvidia and not nv?

Yep!

---

### Post by tseliot on 2006-08-28
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by handy on 2006-08-29
I get around 5000 fps in glxgears, which I would think is acceptable for this card.

Movies play well, I have no graphic card issues here that I can see, except that I can't change the refresh rate to the correct numbers!!??

The same numbers my other machine here is conected with, to the same monitor.  These numbers came out of the manual that came with the monitor.

Got me stumped!? :confused:

---

