---
title: "Ripping from Multiple DVD Drives"
date: 2009-12-09
forum: Multimedia Software
---

### Post by mathew_davis on 2009-12-09
I am using Ubuntu 9.10 and mythtv .22.  

I have 2 DVD roms on a Pata interface and 1 DVD rw on a sata cable.  When I go to rip it only see's one of these drives.  However when I go to Eject media it pops up a menu asking which drive to eject and that shows all 3 drives.

How can I either get a similar pop up when trying to rip a dvd or how can I set it up to see all three drives to rip from.

I tried ripping from one then while the job was running configure the dvd location to one of the other drives.  The ripping still continued but it seemed the mythtv had lost track of the status of that rip.  I also could not rip from the other drive until the first rip was complete.

Any suggestions on this?  Do I need to edit the menu to have a play dvd1, play dvd2 ect as well as rip dvd 1 you get the picture?  Do I need to modify the code to allow for such a pop up menu to be displayed for ripping?  Do I need to setup a script that will spawn a new process for riping one drive and then add the menu items that call these scrips to rip the dvd and just not see the status in mythtv?

Thanks in advance,
Matt

---

### Post by SuperSonic4 on 2009-12-09
I believe CLI handbrake has the ability to rip from multiple drives if you run each task in a separate terminal/tab

---

### Post by mc4man on 2009-12-09
If the dvd's in question didn't contain structure protection (or a very 'mild' protection) and you wanted a rip to file (VIDEO_TS), then vobcopy can be set to autorip from multiple drives, either in the background or in a visible terminal(s). ( visible terminal is best

In other words insert dvd, rip starts, insert more dvd's, also ripped automatically.

If that's what you had in mind I'll describe

---

### Post by mathew_davis on 2009-12-10
So i took a look at HandBrake but it looks like it only converts to MKV or MP4's.  Is there a way to just go straight to VOBs?

What does MythVideo use to rip?  Does it use VobCopy?  If not how do you call the MythVideo ripping software from the command line?  

Is there a way to use VobCopy with LibDVDCss to unencrypt the dvds?

---

