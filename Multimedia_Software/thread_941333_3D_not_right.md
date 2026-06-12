---
title: "3D not right"
date: 2008-10-08
forum: Multimedia Software
---

### Post by glenngds2007 on 2008-10-08
MOBO Gigabyte GA-MA74GM-S2H
Graphics processor on board video
ATI HD2100

The 3D is there what is wrong is that it blinks out to a black screen.  3D effects are just fine with Windows Vista.  Is there any tweaks to fix this problem???????:confused:

---

### Post by patrickballeux on 2008-10-08
Do you have Compiz enabled?  If so, turn it off...

Your problem is that the ATI driver is not working well when Compiz Effects are turned on and other opengl softwares (games).

You should complain to ATI/AMD about that.

I have an ATI x1200, and I've been fighting for a long time on this issue... :)

---

### Post by glenngds2007 on 2008-10-08
Yes compiz is turned on and I will turn it off immediately and then give my 3D apps a try

---

### Post by glenngds2007 on 2008-10-08
I just did not turn compiz off--I completely removed it and then rebooted and now 3D is just fine with the exception of only one game (gl-117).

---

### Post by patrickballeux on 2008-10-08
You just have to disable it, but can leave it installed anyway.  See the "System-Preference-Appearance"...

As for GL-117, I don't know.  Have you installed the latest driver from ATI/AMD (Version 8.9)?  

You can install the EnvyNG that will do that.

---

### Post by glenngds2007 on 2008-10-08
There seems to be a disagreement between Gigabyte and AMD as to what is on and in my motherboard.  AMD says my MOBO has a 780G chip set and Gigabyte says it is a 740G chip set.  AMD says that my MOBO should have a HD2400 GPU and Gigabyte says that it is a HD2100 GPU.  The problem is that the two should use different divers.  Enough of that B*S* how can I tell for sure what is in my computer and therefore know for sure which Driver to download.

---

### Post by patrickballeux on 2008-10-08
run "lspci"

You will see the the description from your periphericals.

Also there is "sudo lshw" which will give great details about your hardware...

---

