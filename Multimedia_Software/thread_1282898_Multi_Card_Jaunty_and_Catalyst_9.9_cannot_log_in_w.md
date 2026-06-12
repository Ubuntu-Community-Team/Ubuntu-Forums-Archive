---
title: "Multi Card Jaunty and Catalyst 9.9 cannot log in with disabling DRI"
date: 2009-10-04
forum: Multimedia Software
---

### Post by dalekleader on 2009-10-04
I could not count how many times I have found a resolution on this forum.  But unfortunately I have come up short with this one.  There are 2 parts to this problem.  I would like to have them resolved in order.  Thank you.

Part 1:
I am trying to setup 4 ATI Radeon 4850 video cards to drive 8 monitors.  The problem is once I add more then 1 video card the PC crashes, freezes, locks (pick your word) after I login.  No gnome, no desktop just a black screen.  The workaround I have for the next week was to add option "DRI" off" in xorg. As a result I have poor/low 2D performance and no 3D at all.  But I can login and launch applications.

What I would like is great 2D performance.  3D would be a bonus but not a necessity.  

Part 2: 
The current configuration is each pair of monitors on each card is mirrored.  The ideal would be to allow an application like video to span over all of the monitors.  Xinerama seems to lead in the right direction but has limits to the boundaries of the monitor pair on a single video card.

Problems to solve in order of priority:
1) Gain back my 2D acceleration with 2 or more video cards.
2) Setup a way to span a single application over all 8 monitors.

Now, the system is currently in use at site and will not get it back for about a week.  As I wait I would not mind fielding some ideas from the community.

---

### Post by markbuntu on 2009-10-05
Are you using the latest driver from ati?
Are you using the Catalyst Control Center?

You cannot use xinerama with randr enabled (RandR1.2 is incapable of dealing with multiple gpus. The soon to be released 9.10 driver makes it a lot easier to set up multi gpus.

But for now in the Device section of xorg.conf you need to add this line to diable randr

Option   "EnableRandR12" "false"

Then you can use xinerama.

---

### Post by dalekleader on 2009-10-05
Thanks for the reply.
I am using all of the latest.  Catalyst 9.9.  COnfiguration was simple:

> aticonfig --initial -f --adapter=all

The xorg.conf was fairly lean but DRI had to be off otherwise X would fail.  It would be great to know if others are having trouble with Catalys 9.9 with DRI?

Thanks for the tip to disable RandR12.  I guess I miss interpreted what the readme notes from ATI meant when they said improved RandR12 support.  I will try that when I get the unit back.

---

### Post by markbuntu on 2009-10-06
The 9.10 driver will be out soon, you use it because it has nuumerous fixes for multi-gpu. Like it takes care of randr automatically when you enable more than one gpu,

---

