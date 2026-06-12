---
title: "Mythbuntu 9.04 Problems after start"
date: 2009-06-30
forum: Mythbuntu
---

### Post by brian_hayward on 2009-06-30
I just installed Mythbuntu 9.04 and when i start the machine up i get to the login screen, enter my user name and password, and it looks like it is loading all of the components.  I even see the "Application" button in the upper left hand corner and the time in the upper right corner as well as the internet icon next to the clock.  After a few seconds though the screen goes blank and i cant see anything.  I tried numerous key combinations on my keyboard and the administrative password box (the password box that we get when we are changing something and need administrative permissions) comes up so i know the computer isnt locked up.  Any suggestions/ideas on how to fix this is greatly appreciated.  thanks.

---

### Post by brian_hayward on 2009-07-26
> **brian_hayward said:**
> I just installed Mythbuntu 9.04 and when i start the machine up i get to the login screen, enter my user name and password, and it looks like it is loading all of the components.  I even see the "Application" button in the upper left hand corner and the time in the upper right corner as well as the internet icon next to the clock.  After a few seconds though the screen goes blank and i cant see anything.  I tried numerous key combinations on my keyboard and the administrative password box (the password box that we get when we are changing something and need administrative permissions) comes up so i know the computer isnt locked up.  Any suggestions/ideas on how to fix this is greatly appreciated.  thanks.

I posted this thread a few weeks ago but didn't get any hits.  I reinstalled Mythbuntu 8.10 and everything worked fabulously.  i tried to upgrade and now I'm getting the same problem.  However this time around i am able to exit the Mythbuntu and use the underlying operating system like normal.  I open other applications and they work fine.  Any help or suggestions would be greatly appreciated...pleas obi wan, help me.

---

### Post by MythMaker57 on 2009-07-26
Have tried redoing the Xorg configuration ? Try this...
sudo dpkg-reconfigure xserver-xorg

Often I had to start Mythbuntu in failsafe mode and redo the 
Xorg configuration to get it to work...

---

### Post by chipppy on 2009-07-27
Good Afternoon

dont know if this is related but I ran into a black screen problem when I first installed 9.04.
The fix was to start up in safe mode and update and activate the navida drivers to the recommended one (the non-GPLdriver though). 

This fixed my problem and I have not had any problems since.

Cheers
chipppy

---

### Post by brian_hayward on 2009-07-27
> **MythMaker57 said:**
> Have tried redoing the Xorg configuration ? Try this...
sudo dpkg-reconfigure xserver-xorg

Often I had to start Mythbuntu in failsafe mode and redo the 
Xorg configuration to get it to work...


What parameters in the Xorg configuration do I have to change?

---

