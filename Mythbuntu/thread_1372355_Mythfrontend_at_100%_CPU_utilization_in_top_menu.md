---
title: "Mythfrontend at 100% CPU utilization in top menu"
date: 2010-01-04
forum: Mythbuntu
---

### Post by mathog on 2010-01-04
I just noticed that when mythfrontend is in many menus it uses 100% CPU.  This is a dual core system, so it trundles along on the other core when this happens.  The system is mythbuntu 8.10 and JY Avenard's 0.21 VDPAU version, using OpenGL and the default theme.  It seems that any menu which is like the top menu (a single list of 5 or so options to choose from) does this.  The more complex menus, like the one to delete recordings, use much less CPU time.

I do not recall it doing this when it used TV-OUT, but may just not have caught it.  Currently it uses 1920x1080 output through a DVI connector.  Nvidia 8400GS card.

Off the top of my head it looks like it is spinning on an event read, with no short "sleep" in the loop to reduce the CPU load.

Anybody else seen this?

---

### Post by ahood on 2010-01-04
I had high CPU utilization (>80%) with OpenGL enabled in the Frontend settings, even with an Nvidia graphics card and Nvidia 3d drivers installed. CPU utilization decreased to <10% after disabling this option in the frontend settings. 

Hope this helps.

---

### Post by mathog on 2010-01-12
> **ahood said:**
> I had high CPU utilization (>80%) with OpenGL enabled in the Frontend settings, even with an Nvidia graphics card and Nvidia 3d drivers installed. CPU utilization decreased to <10% after disabling this option in the frontend settings. 


You are correct, switching from OpenGL to QT does eliminate the load in the menu.  Unfortunately when the system uses QT instead of OpenGL it eventually locks up in the EPG, and that is worse.  Good thing there are two cores in this CPU...

---

