---
title: "Blank desktop on startup -- no menus or icons"
date: 2010-04-06
forum: Mythbuntu
---

### Post by yzfr1 on 2010-04-06
I recently ran the update manager and rebooted.  Since then my frontend does not display anything but just a blank background image...

I am have 9.10 installed

uname -a 

2.6.31-20-generic #58-Ubuntu 

I have looked in the Xorg logs but can't find anything.

I don't know where else to look.  Please help..


Attached is an image taken from VNC viewer.

---

### Post by volkswagner on 2010-04-06
What type of display do you have?  

Perhaps it is overscan on your tv and/or resolution setting is incorrect, putting menu's and task bar off screen.

I have the same issue with SD TV via S-video, but with the current setting it allows maximum view of mythtv setup screens.

Just a thought.

EDIT:  Hmn...Not so sure this would transfer to a VNC session...

---

### Post by yzfr1 on 2010-04-07
> **volkswagner said:**
> What type of display do you have?  

Perhaps it is overscan on your tv and/or resolution setting is incorrect, putting menu's and task bar off screen.

I have the same issue with SD TV via S-video, but with the current setting it allows maximum view of mythtv setup screens.

Just a thought.

EDIT:  Hmn...Not so sure this would transfer to a VNC session...


Well that is another problem all together...   I am using a 1080i flat screen (Magnavox) TV.  It does not detect this tv correctly.  X will automatically set my resolution to 800x600 when it starts.  In order to even see anything on my screen I have to ssh into the box and change the resolution via command line and xrand.  Then I have to use VNC to go to the nvdia gui and change it to interlace mode to even see the screen on this tv.

However, I can't see anything at all with vnc.  It just gives me the screen where I can move the mouse around but not see anything else.

I have look for many days on this one and I am at a loss.

---

### Post by yzfr1 on 2010-04-08
Alright..  hooked up to a monitor and I still get the same problem..  does anyone have any ideas?

I don't have anything on my screen except my mouse pointer..

---

### Post by funkydan2 on 2010-04-08
What does the screen display during boot up?

Does it show the splash screen whilst you're booting?

Does it show the login screen (or have you configured your machine for auto-login)?

What happens if you bring up a virtual console (press ctl-alt-F2)?

What window manager/desktop environment are you running (XFCE is what mythbuntu uses by default)?

---

### Post by yzfr1 on 2010-04-08
> **funkydan2 said:**
> What does the screen display during boot up?

Does it show the splash screen whilst you're booting?

Does it show the login screen (or have you configured your machine for auto-login)?

What happens if you bring up a virtual console (press ctl-alt-F2)?

What window manager/desktop environment are you running (XFCE is what mythbuntu uses by default)?

It displays the normal boot up screens.  It then goes to loading mythbuntu loading splash screen. (small tv icon). 

It does not show the login screen.  I think it is set to auto login.

If I press crtl-alt-F2 it goes to a command prompt asking for a login.

I logged in once this way but was unable to get back to the desktop.

I believe I am running the default desktop environment which is XFCE.  

Everything was working fine till I did an update.

---

### Post by funkydan2 on 2010-04-09
Since you get the mouse pointer moving on the screen, it sounds like a problem with XFCE. Have you tried deleting* the XFCE settings? I think they're found in .config and .cache?

(*Don't actually delete the directories, just move them to .config.old so that you can restore them if it doesn't help.)

---

### Post by yzfr1 on 2010-04-09
> **funkydan2 said:**
> Since you get the mouse pointer moving on the screen, it sounds like a problem with XFCE. Have you tried deleting* the XFCE settings? I think they're found in .config and .cache?

(*Don't actually delete the directories, just move them to .config.old so that you can restore them if it doesn't help.)


Thanks for you help here funkydan2.... 

I renamed those files..  There seems to be no changed.  It appears they were recreated like they should be.

I agree with you.  I think the problem is with XFCE, but I don't know what to do to fix it.

Any way to reinstall XFCE?

---

### Post by rxbandit on 2010-04-29
Having this same problem. Were you able to solve this?

---

### Post by saliflo on 2010-04-29
same problem.

---

### Post by cgroza on 2010-04-29
If you upgraded via update manager then I suggest making a clean install because a lot of people have video problems after upgrade.

---

### Post by saliflo on 2010-04-30
I made clean install several time, as beta, RC and final release. Problem is continuining.

---

### Post by John Bennett on 2010-10-14
I have the same problem.

I added Mythbuntu to my existing Ubuntu installation.  When I log in, I get a blank desktop with nothing but a clock.

---

### Post by GuiGuy on 2010-10-14
Are you referring to updating a particular version or are you upgrading?

I'm asking because the good guy in my head is saying "Don't upgrade to 10.10, 10.04 is working great!". The other guy, the one in black with the devilish grin, is saying, go on, have a go. What could possibly go wrong?

---

### Post by jeff@snowflight.com on 2011-01-08
I have the same problem after upgrading from 9.04 to 10.04.1

I have enabled the autologon and myth front end is starting in console 1, but for some reason after it starts, the system switches to console 2.

I am fine if I simply Control-F1 back to first console.

How can I make it stay on console 1?

Thanks,

Jeff

---

