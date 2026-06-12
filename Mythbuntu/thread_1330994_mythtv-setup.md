---
title: "mythtv-setup"
date: 2009-11-18
forum: Mythbuntu
---

### Post by pinacate on 2009-11-18
How do I launch mythtv-setup after I've gone through the install process? I want to rescan input channels etc.

Are there keyboard shortcuts for launching setup and start/stop the backend etc.

Many thanks,

---

### Post by shifti on 2009-11-18
Either open a terminal and type ```
mythtv-setup
``` or click Applications - System - MythTV Backend Setup.

---

### Post by pinacate on 2009-11-19
Thanks!
The response from entering "mythtv-setup" in a terminal window was: "Gtk-WARNING **: cannot open display:"

Also I'm really curious about your other suggestion of "Applications - System - MythTV Backend Setup" as I don't see any menu item "Applications". Is this in the same menu list as "Watch TV"?

---

### Post by larsolav on 2009-11-19
> **pinacate said:**
> Thanks!
The response from entering "mythtv-setup" in a terminal window was: "Gtk-WARNING **: cannot open display:"
Are you running X when you do this?

> **pinacate said:**
> Also I'm really curious about your other suggestion of "Applications - System - MythTV Backend Setup" as I don't see any menu item "Applications". Is this in the same menu list as "Watch TV"?

Ah- this is on the Ubuntu desktop, not in the Myth Frontend menus... So exit the frontend and select "Applications - System - MythTV Backend Setup"

Good luck to you!

---

### Post by Barry_IA on 2009-11-19
> **pinacate said:**
> How do I launch mythtv-setup after I've gone through the install process? I want to rescan input channels etc.

Are there keyboard shortcuts for launching setup and start/stop the backend etc.


To rescan channels go to your Desktop (quit MythTV), Applications > System > Mythbuntu Control Center > MySQL > Launch MythTV Setup > #5 Channel Editor.  Use "Channel Scanner" to repeat a scan for a specific source.  So if you have more than one tuner you need to do this for each tuner.  A dual tuner card has two tuners.

I don't think there are any shortcut keys within MythTV -- not sure why you'd want to but suppose could be set up via the Edit Keys option.  ...Hitting the Escape key pops up a message to verify quitting, which then goes to the Mythbuntu Desktop.

---

### Post by pinacate on 2009-11-19
Thank you all. That solved that problem, now onto the next!

To get to the "Applications" menu you just keep hitting escape until you're asked if you want to exit Myth. Then exit and theres the "Applications" menu. My problem was that I was using ctl-alt-f1 to get to a terminal window and that was shutting down X.

---

### Post by Barry_IA on 2009-11-20
> **pinacate said:**
> Thank you all. That solved that problem, now onto the next!

To get to the "Applications" menu you just keep hitting escape until you're asked if you want to exit Myth. Then exit and theres the "Applications" menu. My problem was that I was using ctl-alt-f1 to get to a terminal window and that was shutting down X.


It's easy when you know the answers! <laff>  I happened to be looking for a lead on a small problem here when stumbled on your question.  Happened I had retyped my installation notes (Mythbuntu version 9.10 requires a few extra steps with the HVR-2250 card I'm using, over the previous version), and your question was one of the items with a slight alteration.

---

